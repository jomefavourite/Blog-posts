## Callback Functions and Higher-Order Functions

Hello! This article is a follow up with my series [JavaScript: The Hard Parts v2 Cover](https://favouritejome.hashnode.dev/series/javascript-the-hard-parts) from a course I took from [Frontend Masters](https://frontendmasters.com/courses/javascript-hard-parts-v2/) By [Will Sentance](https://twitter.com/willsentance).

---

Before we move into Callbacks and Higher-Order Functions, let's know what a Function is all about first.

## Why do we really need Functions?

Firstly, a Function is just a block of code that performs a particular task when invoked and is stored in memory to be used as many times as needed, preventing replication of similar code.

To really understand why we need functions, lets look at these examples below:

### Example 1: <span id="example1"></span>

```
function add9to9() {
  return 9 + 9
}

add9to9()  // 18
```

### Example 2: <span id="example2"></span>

```
function add5to5() {
  return 5 + 5
}

add9to9()  // 10
```

Both functions above are basically returning the addition of the same numbers but both numbers are specific to their function. And that's not really productive since **Functions** are to help us not repeat ourselves.

<hr>

### Example 3: <span id="example3"></span>

```
function addSameNum(num) {
  return num + num
}

addSameNum(4) // 8
```

Looking at the example above, the function `addSameNum` is taking an argument value `4` and returning the sum of the value passed to the parameter `num`. Doing this makes a big difference because we don't have to write separate functions to perform similar tasks, instead just one.

> Parameters (placeholders) are named variable, (from the example above `num` is the parameter) stored in memory and isn't assigned a value until the function is invoked and passed an argument value.

> Arguments are values passed into a `function` parameter when invoked.

From [Example 1](#example1) and [2](#example2), the Function body is basically doing the same thing with different literal values, and it breaks the Principle **DRY - Don't Repeat Yourself.**

So that's why [Example 3](#example3) is a much better approach, but wait a sec, is it the best approach, what if I'll like to add two different values, and also, would like to multiply these values and also add the values if needed.

Interesting right, how can we write one function to do all those instructions above when invoked? That's where **Callback Functions** comes into play.

Here some guidelines you should note about __Callback Functons__.

There's a saying Functions are _first class citizens / objects_. Meaning function are basically **Objects** and can do what *Objects* can do.

1. Functions can be assigned to variables and properties of other objects.
2. Functions can be passed as arguments into functions.
3. Functions can be returned as values from functions.

## Callback Functions

Callback Functions are function(s) inserted into another **Function.** Example:

```js
[1,3].forEach(callbackFunction)

const callbackFunction = (item) => {
   console.log(item)
}
```

From the example above,  the function named `callbackFunction` is a Callback Function, which was invoked inside the function `forEach` making it an Higer-Order Function.

## Higher Order Functions

Higher Order Functions are Functions that takes in a function as parameter values or returns a function.

Now that we know what Callback and Higher Order Function are, let's look into Examples to explain the terms.

Here is a function below, which makes [Example 1](#example1) and [2](#example2) even more reusable:

### Example 4 <span id="example4"></span>

```
function doOperation(input1, input2, instruction) {
  return instruction(input1,input2)
}

function add(val1,val2) {
  return val1 + val2;
}

function multiply(val1,val2) {
  return val1 * val2;
}

doOperation(2,3,add)       // 5

doOperation(2,3,multiply)  // 6
```

Wow! The first `function: doOperation` looks daunting right? Allow me to simplify it by showing how Javascript reads the instruction.

![pic1](https://jomefavourite.github.io/Images/callback1.jpg)

From the illustration above, the functions are stored in the **Global Memory**.

> Note: Javascript doesn't know what's in the function body yet, until it's invoked. <br><br>
Execution Context has been discussed [here](https://favouritejome.hashnode.dev/execution-context-and-call-stack).

On calling `doOperation(2,3,add)` a Function Execution Context is created and `doOperation()` is added to the **Call Stack**

![pic1](https://jomefavourite.github.io/Images/callback2.jpg)

The parameters hold the values passed as _arguments_, which are `2,3,add` and stored in the **Local Memory** for the function.

Inside `doOperation(2,3,add)` function body, `instruction` has the value **add** and the function is to return `instruction(input1, input2)`. Javascript has look for the value passed to `instruction` because it's just a placeholder in memory.

Since the value is **add**, we could replace `instruction(input1, input2)` to `add(input1, input2)`. But remember `input1` and `input2` are also placeholders and have been assigned values.

So, it could be written as `return add(2,3)`, which was `return instruction(input1, input2)`. Now, Javascript checks the **Local Memory** of `doOperation()` if `add` function exist and it doesn't. Then, it moves to the **Global Memory**, which does have `add` function.

Since add function exist (`add: function`) in the **Global Memory**, it's then invoked, whereby creating a _Function Execution Context_ and added to the **Call Stack**.

![pic3](https://jomefavourite.github.io/Images/callback3.jpg)

> `val1, val2` as parameters in the `add` function are replaced with the values of `input1, input2`. 

When the returned value is got from `add function` which will be `5` in this case, the `add()` Function Execution Context is deleted, also in the Call Stack.

Then, the returned value is passed to the `doOperation` function as it's returned value.

That's a lot to comprehend, right? All that Javascript does behind the scene. I've got to say these concepts are pretty much difficult to grasp.

> Mind you, there are a lot of applications to Callback Functions and Higher-Order Functions, but I'll stop here.

Hey! it's time for a quiz 😁, after going through all these, could you tell which function is the **Callback Function** or **Higher Order Function**?

- doOperation() is the Callback Function
- add() is the Higher Order Function
- doOperation() is the Higher Order Function
- add() is the Callback Function

Comment below, I'll love to know your answers.

> Hint: there are two answers

For more understanding on Higher-Order Function, I'll suggest you read a [blog](https://blog.oshogunle.com/learning-javascript-topic-higher-order-functions-ckdvlkqxs0151jas1fl8tdx13) by @omotola

**Thanks for reading.**


