---
title: "Principles of JavaScript"
datePublished: Wed Sep 16 2020 09:55:13 GMT+0000 (Coordinated Universal Time)
cuid: ckf57lm3y02evpos1e6trd384
slug: principles-of-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1600346915197/JRvIebY8f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1600344413275/_dKGTvOiR.png
tags: javascript

---

Hello everyone, In this article, I'll be sharing my jottings from a course I recently took from Frontend Masters : [JavaScript: The Hard Parts, v2](https://frontendmasters.com/courses/javascript-hard-parts-v2/).

I'll be documenting what I've learnt throughout the course for reference later on and also sharing it with you guys.

> Side note, this is my first tech blog, I'm so excited 😊. 

<hr>

I'll begin, by explaining 
how JavaScript execute and run code, which leaves us to the:

- Thread of Execution and
- Memory

## Thread of Execution
The term "Thread of Execution" simply means Javascript goes through the code line-by-line and then runs/execute each line as it goes. Which makes Javascript, a Synchronous Language.

Now you might wonder, what's Synchronous?

> Synchronous simply means executing one instruction completely before moving to the next instruction.

Okay then, let's walk through this the code below: 

```js
var fruits = ["orange", "apple", "mango", "pineapple"]
hello everyone
fruits[3]
console.log(3)
``` 
Looking at the above example, if it were to be run on the browser's console. 
The first line is checked and valid cause Javascript recognizes that's that variable fruit that has an array as the value.

Meanwhile, as soon as line 2 is got to, instantly on the console you'll get : 

```
Uncaught SyntaxError: Unexpected identifier
``` 
Hereby Javascript is saying, I don't know what you mean by `hello everyone and then at line 3 - `fruits[3]` isn't executed and any other statement below wouldn't be executed.

To sum up the discussion on Thread of Execution. Javascript goes through a code line-by-line and execute each line, if there's an error on a line like at line 2, from the above example any other Javascript statement valid or not below the error isn't going to be executed.

> Try it for yourself

## Memory 
There're two expects to the Memory, which are:

- Global Memory
- Local Memory

And all the Memory does is to save **data** like strings and
arrays even functions, so we can use that data
later in its **memory**.


For example, we have an array:

```
var fruits = ["orange", "apple", "mango", "pineapple"]
```
Then the variable `fruits` is stored as a label/placeholder name on the Memory containing an array. So whenever we need the variable `fruits` we'll making a reference to the array stored in Memory.

Here's a visual view of how the variable is stored in Memory:

```js
fruits: ["orange", "apple", "mango", "pineapple"]
```
>Note: this example is being stored on the Global Memory.

### Global Memory
Every line of code/instruction written that's not executed in a function is stored on the Global Memory. That's why the variable `fruits` declared earlier is stored on the Global Memory from the above example.

### Local Memory 
Before I dive into Local Memory, let's look at the code below:

```
function adding(num) {
     var name = "Favourite";
     let age = 30;
     return num + 2
}

adding(4)     //Output : 6
```
A function adding has been declared/defined and stored on the Global Memory. 

Virtualized like this :
```dir
adding: function
```
When the function `adding(4)` is called on line 6, an Execution Context is created which will be discussed in the next article. Also, a Local Memory is created to store data that exist in the function body only.

The Thread of Execution which executes the code/instructions line-by-line goes into the function body `adding` and execute each line.

Line one (1) in the function body `adding` 
```
var name = "Favourite";
```

Representation in memory:

```
name: "Favourite"
```
The variable `name` is a placeholder name/reference in memory that has the value "Favourite". And so on for the rest lines irrespective of **var** and **let** in the function body.

A more precise illustration of what's stored on the Local Memory is shown below:

```dir
num: 4
name: "Favourite"
age: 30
```
>  Note: I'm not 30 years old 😁 and the returned value isn't stored on the memory.

From the illustration above the parameter **num** in the function `adding` is being assigned a value 4 which is the argument passed and **stored first** on the Local Memory before anything else. <br> Then **name** and **age**.

Now the Thread of Execution is at line 3 in the function body `adding` which return a value `return num + 2` .<br>
 `4 + 2 = 6` ... outputs 6 to the console. 

After all the lines of code in the function `adding` body has been executed, that function forgets its parameter value and anything stored in the Local Memory until invoked/called again and then a new argument will be passed to the function or not.
 

## Thanks For Reading


 