## What's Asynchronous JavaScript‽


Hello! Welcome back to my series, [JavaScript: The Hard Part cover](https://favouritejome.hashnode.dev/series/javascript-the-hard-parts). If this is my first post in the series you're reading I'll advise you to take a look at the previous articles to follow up with the series.

## Previous Blogs
- [Principles of Javascript](https://favouritejome.hashnode.dev/principles-of-javascript)
- [Execution Context and Call stack](https://favouritejome.hashnode.dev/execution-context-and-call-stack)
- [Callback Function and Higher Order Function](https://favouritejome.hashnode.dev/callback-functions-and-higher-order-functions)
- [What's Closure in Javascript](https://favouritejome.hashnode.dev/whats-closure-in-js)

<hr/>

## Introduction

In this article, I'll go through Asynchronous Javascript, Web API, Callback queue and the Event Loop based on my understanding of the different topics. Please reach out to me if I write anything wrong.

Let's dive into the topic:

**Asynchronous** simply means having different actions happening at the same time in any other without waiting for each other 
 which is applicable to **Asynchronous Javascript**.

You should note Javascript is actually a **"Synchronous"** language whereby you might have heard the saying _"JavaScript is a Single-threaded language"_.

The statement above simply means Javascript can only perform one operation at a time before moving to the next operation.

And you might have also heard the saying _"Javascript is a single-threaded language that could be none blocking"_.

Hmm, what does **non-blocking** mean?

Well, that's where "Asynchronous" comes into play, which allows Javascript to perform multiple tasks meanwhile a task is waiting to be performed. More explanation later on.

![mindblow](https://media.giphy.com/media/xT0BKCxTX64gcYNuwg/giphy.gif)

For instance; On Twitter, you click on the like button meanwhile your internet speed is slow and Twitter hasn't acknowledged your click. Also, you click on another like button even though the first one hasn't been acknowledged. And then you comment on a post and send it.

> Note: you've done three operations now, clicking on two like buttons and send a comment. Also all the operations are pending meaning the action hasn't been saved on Twitter database.

![clickclick](https://media.giphy.com/media/l0HlQXlQ3nHyLMvte/giphy.gif)

You've done three things now, none of them has been acknowledged by Twitter because of the poor internet connection. 

Later on, the internet becomes good, the first like button you clicked on will be acknowledged then the next before the comment.

Meanwhile, while the internet was poor and the feeds were loaded and you were able to interact with Twitter and not have to wait for your likes to be acknowledged before further interactions.

From the scenario above, it's all **Asynchronous Javascript** that making this work. If not you'll have to wait for the first instruction before the next.

## What does Asynchronous JavaScript entails

- Promises
- Web Browser features (API)
- Microtask queue
- Callback queue / Event queue
- Event loop etc

> For this article, I'll be looking into Web Browser features, callback queue and the event loop.

## Web Browser Features (WEB API)

As it is well known, JavaScript runs on the Web Browser and the Browser has some features that aren't JavaScript but can be interacted with using Javascript known as the WEB API.

**Some Web Browser Features**

- console
- Developer tool
- Timer
- Network Request
- DOM (Document Object Model) and many more

All these features can be interacted with using Javascript with given functions known as **Facade Functions**.

Facade Functions include:

- setTimeout() labeled as Timer in the browser
- clearTimeout() labeled as Timer in the browser
- setInterval() labelled as Timer in the browser
- addEventListener()
- document.qetElementsById() labelled as DOM in the browser and so on.

Before going further in today's topic, you'll need to know about the **Callback queue**

## Callback queue or Event queue

Callback queue is a stack that holds data temporarily and returns the first data it holds following the "First In First Out" principle. The callback queue holds data like setTimout, setInterval and so on (mainly asynchronous data) which are later on pushed to the Call Stack.

Now lets go through this example.<span id="example"></span>

```
function printHello() {
  console.log("Hello")
}

setTimeout(printHello, 0)

console.log("First")
```

Looking at the example above, what do you think will be displayed on the Browsers console?
Take a few minutes to ponder on it.

> I'm assuming you already know what setTimeout() does. Well, if not, setTimeout() takes in a function (callback) then the duration, for the function to be delayed before it is executed automatically.

Let's look at the statements together

- Firstly, a function `printHello()` is stored in the Global Memory.
- `setTimeout(printHello,0)` this line of code is saying send `printHello` which is a label for `printHello()` function to the WEB API feature (Callback queue). It took 0 ms for `printHello` to be sent to Callback queue.
- "First" is then logged to the browsers console.

> Note: Even though the console doesn't belong to Javascript itself and it's part of the WEB API, it's **synchronous**.

```
// Output

// First
// Hello
```

But, why is the `output` so? You may ask.

Looking at the [Example](#example), the duration is `0 ms`, why wasn't `Hello` logged first?

Well, `setTimeout` is asynchronous and it gets added to the **Callback queue** waiting for all synchronous instructions to run first, in this case, `console.log("First")`.

So you might ask, what checks if all synchronous instructions have been run?

That'll be the **Event Loop**.

## Event Loop

The event loop checks if the Call Stack is empty and if there is any data in the Callback queue continuously while Javascript instructions are being executed. When the Call Stack is empty and there exists data in the Callback queue, the data or instruction is pushed to the Call Stack.

> Checkout this article about [Callstack](https://favouritejome.hashnode.dev/execution-context-and-call-stack)

From the [example above](#example), `setTimeout()` adds the function label (printHello) to Callback queue.

Then `console.log("First")` is pushed to the Call Stack and executed (then popped off), since all synchronous instructions must be done first before asynchronous instructions `console.log("Hello")` is not logged.

Now, the Call stack is empty, `printHello()` is then pushed to the Call Stack and the browser logs `Hello`.

## Conclusion

All synchronous instructions must run first before asynchronous instructions. So in a case where you have thousands of (let's say) `console.logs` then a `setTimout()` with `0 ms` duration, all `console.logs` will be executed first before `setTimeout()`.

> Just to be clear once again, I'm no pro at these concepts. I'm just sharing what I've been taught and learning in the process. Hope you've learnt something.

Here are some blogs I read as a reference, you should check them out:

- [Javascript Event Loop - Why so Serious!](https://hashnode.com/post/javascript-event-loop-why-so-serious-cjugdp0fm002j70s1nimnlaq7) By @[Tapasya Gharat](@Tapasya)
- [What is Event Loop in JavaScript?](https://blog.skay.dev/javascript-event-loop-explained) By  @[Skay](@skay)

### Thanks for reading, see you at the next article 😉.
