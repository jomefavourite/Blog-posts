## What's Closure in JS?

Hello once again, before I proceed,  I'll advise you to go through my previous blog posts in this [series](https://hashnode.com/series/javascript-the-hard-parts), because the previous blog posts will aid you to understand the process of JavaScript Execution before Closure. 

But if you're just reading to refresh your memory on the topic _Closure_, then no need to over the previous articles.

## Previous Blogs
- [Principles of Javascript](https://favouritejome.hashnode.dev/principles-of-javascript)
- [Execution Context and Call stack](https://favouritejome.hashnode.dev/execution-context-and-call-stack) 
> I suggest you take a look at this article.

- [Callback Function and Higher Order Function](https://favouritejome.hashnode.dev/callback-functions-and-higher-order-functions)

<hr>

Before I'll get into what _Closure_ is, let's take a look at **Scope** cause it essential to note before *Closure*.

## Scope

Scope is anywhere your variable is being accessed simply, any variable declared outside a function belongs to the _Global Scope_ meanwhile, any variable declared in a function belongs to the _Local Scope_ of that function.

Here is an example to explain what Scope means:

```
// Global Scope
const a = "Hello"

function func() {
  // Function Scope
  const a = "hi"
  console.log(a, "Function Scope")
}

func()

console.log(a, "Global Scope")

// Output
// "hi" "Function Scope"
// "Hello" "Global Scope"
```

To make my point clear, I used a constant variable `const a` which when assigned to a certain value, shouldn't be able to get re-assigned.

But from the example above, there exist a variable `const a` in the **Global Execution Context** (_Global Scope_) and also there exist another variable `const a` in the **Function Execution Context** (_Local Scope_).

Both constant variables have different values because they belong to different scopes.

> `let` variable also belongs to the Scope which it is declared in, unlike the `var` variable.

**Here's a key point you should note:**

> A Function Scope or Local Scope has access to its parent scope. The parent scope could be either another Local Scope or the Global Scope.

Let's look at this example to buttress my point above:

```
var first = 1

function func1(num) {
  var value = first + num

  function func2() {
    value = value + num
    console.log(value) // 5
  }

  return func2();
}

func1(2)
```

![closureImg1](https://jomefavourite.github.io/Images/closure1.png)
![closureImg1](https://jomefavourite.github.io/Images/closure2.png)
![closureImg1](https://jomefavourite.github.io/Images/closure3.png)

🙄 The example looks scary, right? Probably not or otherwise 😉.
Allow me to demystify the above instructions.

> Note: When a function is invoked it gets added to the Call Stack

- Variable `first` is at the _Global Scope_ having a value, `1`
- A function `func1` is declared in the _Global Scope_
- Function `func1` is invoked having an argument value `2`
- A brand new Function Execution Context is created, and in it, the first variable that gets stored in the Local Memory is `num` with the value passed as the argument `(2)` which is the `func1` parameter.
- Variable `value` is being assigned to store the values of variable `first + num`. Javascript then asks what's `first` variable, because it doesn't exist in the _Function Scope_, then it checks the _Global Scope_, and sees it has the value `1`.
- Then `first (1)` plus `num (2)` gets added and stored in the variable `value`.
- Next line, a function is defined as `func2` and stored in the Local Memory of the `func1` function.
- The return statement is to return the invocation of `func2()`.
- A new Function Execution Context is created, the variable `value` is being assigned to `value + num` values.
- Both `value` and `num` do not exist in the Local Scope of the `func2` function, so Javascript checks the outer scope which is the function `func1` scope, gets the values assigned to each variable and perform the arithmetic.
- Finally, displays the value as 5 on the browser's console.

> Understanding Scope would help understand Closure, if anything isn't clear comment below. 

Now that we've gone through Scope, let's look into **Closure**

## Closure

If you recall from my previous articles in this series when a function is invoked a **Function Execution Context** is created and deleted when all instructions have been executed. All variables or instructions stored in the _Local Memory_ of the Function is lost.

But what if there was a way, to let functions remember or hold a certain statement (live data), even though the function has been executed.

That's where Closure comes into play, and it all starts by **returning a function by another function.**

```
function createFunction() {
  let two = 2
  function multiply(num) {
    return num * two++
  }
  return multiply
}

var calc = createFunction()
calc(3)    // 6
calc(4)    // 12
calc(5)    // 20
```

Let's look a graphical illustration first:
![closureImg2](https://jomefavourite.github.io/Images/closure-2_1.png)
![closureImg2](https://jomefavourite.github.io/Images/closure-2_2.png)
![closureImg2](https://jomefavourite.github.io/Images/closure-2_3.png)

Here is the explanation:

- `createFunction` function is stored in memory (Global Memory)
- A variable `calc` is declared and a function invocation is assigned to the variable `calc`

> Note: Variable `calc` is expected to have a value or function or object returned by the `createFunction` function. In other to get whatsoever that's to be returned from `createFunction` invocation, variable `calc` is uninitialised for now until it has a value/function/object.

- Since `createFunction()` has been invoked in `calc` variable, a new Function Execution Context.
- Variable `two` is stored in the Local memory and assigned the value 2.
- A function is defined next `multiply` function and stored in the Local Memory of the `createFunction` function.
```
multiply: function
```
> Note: `multiply` function has closure over variable `two` in the `createFunction` function.
- `createFunction` then returns `multiply` which is assigned to the `calc` variable in the Global Scope.

Now, `calc` variable holds a function `multiply` which is to be passed an argument. For simplicity, I'll illustrate what going on :
```
var calc = function multiply(num) {
                  return num * two++
           }
```

It's clear that `multiply` had closure over the variable `two` but how?

### The bond

When a function is defined/ declared in another function it has access/bond to the outer function Local memory.

> In this case, `multiply` function has a bond to the `createFunction` function Local Memory and any variable declared in it.

Now, that we are aware of this, let's look at what the **Backpack** is, which is essential to Closure.

### The Backpack
The backpack holds the live data (what should be remembered) through a hidden property known as [[scope]] which persists when an inner function is returned out.

From the example above, the backpack holds the variable `two` since it's been 
referenced in the inner Function (`multiply`). 

> Note: Any variable declared at the outer function which isn't used by the inner function doesn't have Closure. For example :

```
function outer() {
   let i = 1
   function inner() {
      return console.log(2)
   }
}

var func = outer()
```
In this case, Closure isn't applicable since there is nothing to remember.

### Individual Backpack
If `createFunction` function is assigned to a new variable and invoked, that will be a new Scope and also be a new **Backpack** which doesn't remember what has been run before it. 

Let's look at the example :

```
function createFunction() {
  let two = 2
  function multiply(num) {
    return num * two++
  }
  return multiply
}

var calc = createFunction()
calc(3)    // 6
calc(4)    // 12
calc(5)    // 20

var calc2 = createFunction()
calc2(3)    // 6
calc2(4)    // 12
calc2(5)    // 20
```
 
Wow! A lot we have been through but if you've read so far, thanks, I really appreciate it.
But you should know I'm no pro at this concept just sharing how I understand **Closure**, there are still a lot of Closure offers but this is just the basics, so I'll recommend more articles to read on.

Here are other great articles on this topic: 
- [Understanding Closure with Javascript with example](https://blog.greenroots.info/understanding-javascript-closure-with-example-ckd17fci5001iw5s1fju4f8r0) By @[Tapas Adhikary](@atapas)
- [Understanding Closure](https://blog.skay.dev/understanding-closures) By @[Skay](@skay)
- [Part 1: Understanding Closures in Javascript](https://rajatexplains.com/understanding-closures-1) By @[Rajat Jain](@rajat_says)

**Thanks for Reading** once again,
If you find this blog useful please do share and contact me on Twitter [@favouritejome1](https://twitter.com/FavouriteJome1)