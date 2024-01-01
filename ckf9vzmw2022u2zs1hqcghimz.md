---
title: "Execution Context and Call Stack"
datePublished: Sat Sep 19 2020 16:29:02 GMT+0000 (Coordinated Universal Time)
cuid: ckf9vzmw2022u2zs1hqcghimz
slug: execution-context-and-call-stack
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1600519179921/_YaUTWdOq.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1600519183249/zu7JKx5rH.png
tags: javascript

---

Hello once again! This article is a more like a continuation from my [first blog post](https://favouritejome.hashnode.dev/principles-of-javascript), so I'll suggest you check it out first.

> Also, this article is written from the knowledge I've got from [Javascript: The Hard Parts v2](https://frontendmasters.com/courses/javascript-hard-parts-v2/) and by also making researches and reading other blogs.

<hr>

## Table of Contents

- [Function](#function)
- [Execution Context](#executioncontext)
  - [Global Execution Context](#globalexecutioncontext)
  - [Function Execution Context](#functionexecutioncontext)
- [Call Stack](#callstack)

Before diving into the main discussion for this article, let's take a look at Function.

## Function

**What's a Function?**

Simply, a Function is a block of code stored in memory that contain(s) a / several instruction(s) and then returns a value or not, to be used later when invoked.

> Functions make code less repetitive.

E.g.

```
function addingBy2(num) {
   return num + 2;
}
```

> Note: The function above has to return a value, not all functions returns a value.

Functions are meant to be called / invoked / run, in order for the function to be executed.

From my [previous article](https://favouritejome.hashnode.dev/principles-of-javascript), I mentioned, an Execution Context is created when a function is called / invoked.

## Execution Context <span id="executioncontext"></span>

Execution Context is simply the environment within which code is ran.

The Execution Context has two parts to it, which are :

- Thread of Execution
- Memory

> Thread of Execution and Memory has been discussed [here](https://favouritejome.hashnode.dev/principles-of-javascript).

Execution Context are of 2 types, which are:

- Global Execution Context
- Function Execution Context

### Global Execution Context <span id="globalexecutioncontext"></span>

This is created immediately Javascript reads a / series of code.

For example :

```
var name = "Jome Favourite"

function log() {
   console.log("hello")
}

var fruits = ["apple","orange"]
```

From the instructions above, a **Global Execution Context** is created and `name`, `log` (function name), `fruits` with their respective values are stored in the **Global Memory.**

E.g.

```
name: "Jome Favourite

log: function

fruits: ["apple","orange"]
```

### Function Execution Context <span id="functionexecutioncontext"></span>

This is created when ever a function is called / invoked.

Let's look at this example :

```
function simpleCalc(num) {
   let firstNumber = 2
   let secondNumber = 3
   return firstNumber + secondNumber + num
}

simpleCalc(5)
```

From the above example, Javascript goes through the code _`Thread of Execution`_ and sees a function definition on line 1 and then stores the function definition into the **Global Memory** of the **Global Execution Context.**

E.g.

```
simpleCalc: function

```

> Javascript doesn't read what's in a function until the function has been called.

On line 7 where the function `simpleCalc` has been invoked, Javascript checks the **Global Memory** if such a function exists.

If the function `simpleCalc` is found in the **Global Memory**, then Javascript goes to the function body to execute the instructions provided.

> In this case, `simpleCalc` does exist in the Global Memory containing a function.

Since the function `simpleCalc` exist, a **Function Execution Context** is created for it.

![pic1](https://jomefavourite.github.io/Images/pic1.jpg)

*An illustration of the Function Execution Context*
<br>

Let's go through what's happening in the function

- the parameter num in the function is stored in the **Local Memory** having the argument value 5
- firstNumber which is a label / placeholder in the local memory holds the value 2
- secondNumber which is a label / placeholder in the local memory holds the value 3

To the browser's console, the returned value is shown as **10.**

Then the Function Execution Context is deleted / cancelled from the **Call Stack** since the function is done executing.

## Call Stack <span id="callstack"></span>

The term **Call Stack** keeps track of where a function is invoked and then holds _(a better term will be push(s))_ the function until the execution is done and then pop(s) it out from the stack.

Call stack follows "First In Last Out" principle, which simply means what ever function is invoked first, is held on the call stack and there could be order functions invoked from the initial function.

All other functions invoked must be done executing and popped out from the Call Stack, before the initial function is popped out.

For example :


```

function outer() {

   console.log("I'm first")

   function inner() {

      console.log("I'm second")

      function innerinner() {

         console.log("I'm third")

      }

      innerinner()

   }

   inner()
}

outer()

// Output :
// "I'm first"
// "I'm second"
// "I'm third"

```

> This type of Function definition is known as **Nested Functions**.

Wow, that's a lot of functions, allow me break it down.

In the **Global Execution Context** which runs immediately, function `outer` is stored in the **Global Memory**.

For example:

```
outer: function
```

Then on line 13, the function `outer` is invoked, which then creates a brand new **Function Execution Context** and is added to the **Call Stack.**

![pic2](https://jomefavourite.github.io/Images/pic2.png)

![pic3](https://jomefavourite.github.io/Images/pic3.png)

*Allow me try to break down the above illustrations.*


> If you feel the picture isn't clear enough, do comment below.<br><br>
> From the `Call Stack` illustration above `global()` is beneath the Call Stack representing the **Global Execution Context** which is executed first.

- Firstly, inside the `outer function` is `console.log("I'm first")` which is one of the browser's features known as **WEB API**, which means Javascript doesn't really have `console.log` in its language.
  - On line 3, the `inner function` is defined, and stored in the `outer's function` execution **Local Memory**.
  - On line 10, `inner function ` is invoked.
> In this case, Javascript checks if such a function has been defined and stored in memory. <br><br>
Checks the `Local Memory` first on where it has been defined, if it wasn't at the Local Memory of being invoked, then it checks the Global Memory.<br><br>
Yes `inner function` has indeed been defined and stored.

- Since `inner function ` is invoked a new **Function Execution Context** is created and its then added to the **Call Stack.**
  - On the first line in the `inner function` we have `console.log("I'm second")`.
  - Then `innerinner function` is defined and stored in the **Local Memory** of `inner function`.

- On line 8, `innerinner function` is invoked and another Function Execution Context is created and then added to the Call Stack.
  - Here also we also have `console.log("I'm third")` which is held by the browser.


Now that all functions invoked is done executing, the `innerinner function` is popped off the Call Stack and its Execution context is deleted,  follow by `inner function` then lastly `outer function`.

But the browser know it was to display a value to the console, so it displays the initial `console.log` which was `"I'm first"`, `"I'm second"` and `"I'm third"`.

## Conclusion 
Wow! That's a lot to take in, I know right! 😊. But the best or worst part, is that there still other concept that I didn't dive into. So, If you'll like to read more on **Execution Context** and the likes treated in this article, check out this [blog](https://blog.skay.dev/javascript-event-loop-explained) by @skay.

Thanks for reading, this is a long one.

Contact me: [@twitter](https://twitter.com/favouritejome1)