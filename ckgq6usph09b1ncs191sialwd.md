## Understanding Promises in JavaScript: Part 1

Hello once again, this article is all about what I understood from a course I took [Javascript: The Hard Parts](https://frontendmasters.com/courses/javascript-hard-parts-v2/) from FrontendMaster which I've been writing about in this [series](https://hashnode.com/series/javascript-the-hard-parts-v2-cover-ckfb9a3bz04lf2zs1eow666vd).

From the series, so far, I've written about Thread of Execution, Memory, Execution Context, Call Stack, Callback queue, Event loop, WEB API and then Asynchronous Javascript.

I'll advise you to check out the [previous blog posts](https://favouritejome.hashnode.dev/asynchronous-javascript) before proceeding anyway let's proceed.

---

## Introduction

I'll explain what a Promise is, what are the properties a Promise object has and how it's asynchronous.

Now, let's get to the main topic;

### What's a Promise

A **Promise** is a special object that may produce a single value at some time in the future. Since the single value is expected, later on, that makes the concept about _promises_ asynchronous.

Recap from my previous post on [Asynchronous Javascript](https://favouritejome.hashnode.dev/asynchronous-javascript), whenever an asynchronous instruction is to be executed, it goes to the Web Browser and there isn't any way to tell Javascript about the progress of the asynchronous operation before it moves to the Call stack for execution.

But, with **Promises**, you'll be able to tell Javascript the progress of what's going on in the Web Browser's background.

Here's a quote by [Will Sentance](https://twitter.com/willsentance) the instructor of the course: 

> "when you trigger something in the background, don't just throw it out there. But have it have some sort of consequence in JavaScript memory as well"

- _"something in the background"_ means asynchronous instruction
- _"don't just throw it out there"_ this statement is saying don't just add the asynchronous instruction to the Web Browser background
- _"But have it have some sort of consequence..."_ this is tell Javascript the progress of what's going on at the background.

Since it'll be better to have some consequence based on what's happening on the Browser to JavaScript, **Two-pronged facade function** was initialized.

What's meant by **Two-pronged facade function** you might ask:

- Start a request/task in the Web Browser background and
- Return a placeholder object (promise) immediately in Javascript

What request/task you might ask?

In this case, I'm talking about speaking to the internet using **Fetch** / XHR, labelled as Network Request by the Web Browser.

**Fetch** speaks to the internet while in the Web Browser background and then returns a promise object to Javascript. The promise object shows the progress of the data to be fetched.

Let's look at an example:

```js
function display(data) {
  console.log(data);
}

const futureData = fetch('https://twitter.com/jomz/tweets/1')
futureData.then(display);

console.log("Hello");
```

> If you'll prefer viewing an illustration demonstrating the instructions above, click [here](#img)

From the instructions above:

- Firstly, a function `display()` is declared and stored in the Global Memory.
- Then a variable `futureData` is assigned a value `fetch` to go to some **URL** (Uniform Resource Locator) and get a data (response data).

  - The `fetch` returns an object which is a **promise** with three properties/keys (for this article, we'll be looking at two properties) which are:

  1. `value` which has no value for now 
  2. `onFulfilled` which is an empty array for now also.

- `futureData` holds an object (promise object) which is JavaScript consequence of getting something through the internet.

  - The consequence happening on the Web Browser will be a **Network Request** which holds the domain name (`twitter.com`) of the URL and also the path (`jomz/tweets/1`) which the domain name is linked to.

  - > Note: by default `fetch` uses `GET` saying get some data from the internet.

  - When whatever data fetched has been retrieved (known as **response data**), its get added to the promise object `value` property.

> Note: the time taken to speak to the internet isn't known, it could be days on a slow network :) but whenever the **response data** is gotten it'll be inputted (passed as parameter) by default into a function in the `onFulfilled` property.

- `futureData.then(display)`: this line of code is saying, whatever response data that'll be received, should be added to the function `display` in the `onFulfilled` property array of `futureData`, also having access to the `value` property value.

- `console.log("Hello")` is executed next.

- Now, after 200ms, finally the Web Browser has received a response data (`"hi, everyone"`) which is then passed to the `futureData` value property and then the function (`display()`) in `onFulfilled` property is invoked and added to the Call Stack also having the response data as parameter and then logs `hi, everyone`.

> Remember when ever a Function is invoked a brand new Function Execution Context is created, more on that [here](https://favouritejome.hashnode.dev/execution-context-and-call-stack)

OMG 🤯, that's a lot of details. Here is a graphical illustration below of all the above explanations.

 <span id="img"></span>
![img](https://jomefavourite.github.io/Images/promise1.png)

## Conclusion

They're more advanced ways of using promises from the little research I made but this is the fundamentals of what promises is all about.

Here are further concepts to note:

- When the `value` property in the promise object is empty, this state is known as **Pending**.

- When the `value` property in the promise object has a value, this state is known as **Resolved**.

- Lastly, the **Rejected** state is when something has gone wrong with the data that's meant to be recieved. I'll write about this state in the next article.

Also, in the next article, I'll be writing about Microtask Queue and also looking at more complicated example.

**Thanks for reading** 🥳, if you've read to this point, see you at the next article.

> P.S. To be frank, I haven't got my hands dirty with these concept, but I feel learning and sharing what I've learnt will be a great use to me when I finally start appling these concepts or what do you think? Leave in the comment below.
