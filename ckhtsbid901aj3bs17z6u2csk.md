---
title: "Class, Prototype and OOP Concept Explained"
seoTitle: "Class, Prototype and OOP Concept Explained | Favourite Jome"
seoDescription: "There are 4 different ways of storing data (properties) and functionalities (methods) together in one place which can be used multiple times as need."
datePublished: Mon Nov 23 2020 00:01:06 GMT+0000 (Coordinated Universal Time)
cuid: ckhtsbid901aj3bs17z6u2csk
slug: class-prototype-and-oop-concept-explained
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1606089429382/RDEJpSaXv.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1606089431198/lmN2nHU4I.png
tags: oop, javascript, class, hashnodebootcamp, hashnodebootcamp2-1

---

Hello everyone 👋, this article is also part of my series [Javascript: The Hard Parts v2 Cover](https://hashnode.com/series/javascript-the-hard-parts-v2-cover-ckfb9a3bz04lf2zs1eow666vd). Though you don't have to read the previous articles to follow up with this article. But I recommend reading my previous articles in the series 😉.

## Introduction

There are 4 different ways of storing data (properties) and functionalities (methods) together in one place which can be used multiple times as need. In this article, we'll go over the 4 different ways and get to a standard way at least for now to achieve the same goal.

---

Firstly, why do we need objects, have you ever thought of that?

Well, here's a scenario. Let's say you'll like to store some data that belongs to a particular user in your application, probably a profile application. This user has to perform some instructions (functionality) and you want both the functionality and the data of that user to be used by only to that user.

From the scenario, that's where **Objects** comes into play right!

__Example 1:__

```js
const user1 = {
  name: "John",
  dob: 1999,
  age: function () {
    let today = new Date().getFullYear();
    return today - user1.dob;
  },
};
```

From the example above, we have some data (properties) which are `name` and `dob` (date of bate) and a functionality (method) `age` which belongs to that specific user. But what if we'll like to have another user with similar data. Another similar object will be created.

__Example 2:__

```js
const user2 = {
  name: "Sally",
  dob: 2002,
  age: function () {
    let today = new Date().getFullYear();
    return today - user2.dob;
  },
};
```

Now, we have two users `user1`, `user2` having their data (property) and functionality (method) specific to both of them, **but** this introduces repetition breaking the DRY - Don't Repeat Yourself principle.

Since both `user1` and `user2` have `name`, `age` property. Is there a way to avoid repetitions in this scenario?

Yes, you bait there is, then functions comes to your mind right because **Functions** are means of storing data in this case related data to be called several times generating a new output.

## Solution 1: Function

```js
// First way of using a function

function user(name, dob) {
  return {
    name,
    dob,
    age() {
      let today = new Date().getFullYear();
      return today - dob;
    },
  };
}

let user1 = user("John", 1999);
let user2 = user("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```

If you're not used to the syntax above, I've re-declared it to another syntax.

> Syntax above: Object Property Value Shorthand in JavaScript with ES6

But If you understand what I did click [here](#next) to skip the other syntax.

```js
// Second way of using a function

function user(name, dob) {
  return {
    name: name,
    dob: dob,
    age: function () {
      let today = new Date().getFullYear();
      return today - dob;
    },
  };
}

let user1 = user("John", 1999);
let user2 = user("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```
<span id="next"></span>

Here another way of writing the `user` function above:

```js
// Third way of using a function

function user(name, dob) {
  let newUser = {};

  newUser.name = name;
  newUser.dob = dob;
  newUser.age = function () {
    let today = new Date().getFullYear();
    return today - newUser.dob;
  };

  return newUser;
}

let user1 = user("John", 1999);
let user2 = user("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```

__Here's a rundown of the third way of using the function above:__

- A function `user` is declared and stored in the Global Memory.
- `user1` has an invocation to `user()` function and holds what's returned by the function.
  - `name` and `dob` parameter in `user` function holds the argument values `"John"` and `1999` respectively.
  - `newUser` has the value of an empty object
  - `newUser.name = name` : `newUser` which is an object has a property named `name` which holds the `name` parameter value ("John").  
  - `newUser.dob = dob` same procedure as `newUser.name = name`
  - `newUser.age` holds a function/method.  Whereby `age` is the property name.
- `return newUser` : `newUser` object is returned to `user1`

> Same procedure for `user2`.

- `user1.age()`: Since `user1` holds all properties and method from `newObject` it has access to `age()` method which returns `21` when the instructions in the method is executed.

<br>

So now, we've been able to store personal specific details/data using a Function to which returns an object for a particular user with properties and method.

But there is a problem with this approach, what if we'll like to add another functionality (method) to the returned object in the function. Then we'll have to go to the function to add that functionality (method) which isn't efficient.

Also, most importantly the method `age()` is being copied twice, to each user - `user1` and `user2` which is a waste of memory space since it isn't changing, let alone if the object had hundreds of methods to be called.

With that being said, this approach isn't good enough. So the big question now is, is there a better way?

## Solution 2: Prototype Chain

Well yes, there is a better way, which brings about **Prototype Chain**.

Prototype Chain is a way to link/bond to another object where a method/properties could have been declared, which is then accessed through another object.

Hmm! You might be confused, don't worry I'll break the point down.

Meanwhile, to use the prototype chain, we have to call `Object.create()` technique.

```js
function user(name, dob) {
  let newUser = Object.create(ageCalc);

  newUser.name = name;
  newUser.dob = dob;

  return newUser;
}

const ageCalc = {
  age: function () {
    let today = new Date().getFullYear();
    return today - this.dob;
  },
};

let user1 = user("John", 1999);
let user2 = user("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```

Using `Object.create(ageCalc)` returns a new object but also has a bond/link to `ageCalc` object through a hidden property in all objects known as `__prop__` (proto property).

> Note: Firefox browser calls `__proto__` prototype `<prototype>`

**Here's what happens when the instructions above are executed**

- So when the function `user()` is invoked from `user1` variable, a new [Execution Context](https://favouritejome.hashnode.dev/execution-context-and-call-stack) is created and the function `user()` is added to the Call Stack.

- `newUser` variable holds the value of an empty object `{}` but has a bond with `ageCalc` object, having access to the method stored there.

- `newUser.name` means create a key / property name called name. <br>
  Then `newUser.name = name` means assign `name` (as value) got from the `user()` function parameter. <br>
  <br>
  Same procedure for `newUser.dob = dob`.

- ` return newUser` newUser is returned to `user1` variable making it now initialized with `newUser` object.

- Since the function `user` is done executing, it popped off the Call Stack.

> Same process is also carried out for `user2` variable.

- `user1.age()`, JavaScript engine checks `user1` object which was addressed as `newUser` in the function `user`, do I have a method known as `age()` in here, but **no!** so it then goes to the `__proto__` (proto property) if there exist any method like that.

> The process of checking the proto property is known as the **Prototype Chain.**

Yes, there is method `age()` here, which makes `user1.age()` work by invoking the method and returning `21`.

> Same process goes for `user2.age()`

If you'd notice in the `ageCalc` object property `age`, there is a keyword `this`. The `this` keyword makes both `user1` and `user2` have access to `dob` property.

Which is written like this in JavaScript interpreter:

```js
today - user1.dob;

today - user2.dob;
```

> To learn more about the `this` keyword read this article [here.](https://rylexr2678.hashnode.dev/what-is-this-in-javascript) by @[Keshav jha](@rylexr)

Note: `newUser` object returned already has access to `ageCalc` object so `user2` doesn't have to create another method/functionality in other to use `age()`.

This method of encapsulating properties and method is great, we achieve the goal of not replicating our methods multiple times but instead declare it in memory and have it accessed anytime.

But still, is there a much easier way of having the same goal?

## Solution 3: New keyword

The `new` keyword does most of the hard work for us and makes writing much easier.

Here are the hard works we don't have to do ourselves anymore using the `new` keyword:

- Create a new object (in this case a new user object)
- Return the new user object created

So when the function is being called, it will be written like this:

```js
let user1 = new user("John", 1999);
let user2 = new user("Sally", 2002);
```

You might wonder, since we aren't creating the object ourselves, how would we have access/link to `age` method.

Well it turns out, all functions have an object by default and all functions object has a property called `prototype` in them which is also an object.

You can try this for yourself on the console.

```js
function functionObj() {
  return "I'm a function";
}

functionObj.stored = "I'm also an object";

functionObj(); // "I'm a function"

functionObj.stored; // "I'm also an object"

functionObj.prototype = {};
```

Well, the main point here is `prototype` property can be used to store methods and properties.

<span id="solution3"></span>

```js
function user(name, dob) {
  this.name = name;
  this.dob = dob;
}

user.prototype.age = function () {
  let today = new Date().getFullYear();
  return today - this.dob;
};

let user1 = new user("John", 1999);
let user2 = new user("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```

**Here's a break down of the code above:**

- function `user()` is declared

- `user.prototype.age`: in the function `user` object which has the property `prototype` add the property `age` which takes a function/method.

- `user1 = new user("John", 1999)`: create an [Execution Context](https://favouritejome.hashnode.dev/execution-context-and-call-stack) for the function `user`. Then the arguments are assigned to their respective properties.

  - `new user("John", 1999)` the `new` keyword has created an object
  - Notice, `this` keyword in the function `user` body. The object created by the `new` keyword is what `this` keyword is referring to.
  - All properties in `user` function are added to an object and returned to `user1`.

- `user1.age()`: the returned object by `user` function has access/link to the `age` method through the prototype so those `user1` since technically its has the object from `user`.

Hmm! we've come a long way, but there's still one more way of writing the above instructions. Is there anything wrong with the approach of using the `new` keyword?

No, not really. As a matter of fact, the next solution uses the `new` keyword but instead of having a function `user` and a method on the function's prototype could it all be written as one entity.

## Solution 4: Class

Yes, it can. This brought about the `class` keyword, which is a *syntactic sugar* to solution 3.

Example using a Class syntax:

```js
class Users {
  constructor(name, dob) {
    this.name = name;
    this.dob = dob;
  }

  age() {
    let today = new Date().getFullYear();
    return today - this.dob;
  }
}

let user1 = new Users("John", 1999);
let user2 = new Users("Sally", 2002);

user1.age(); // 21
user2.age(); // 18
```

From the instructions above, 

- `class User {}` wraps `constructor()` method and a method `age()`
- `constructor(name, dob) {...}` is basically the same as `user` function at [solution 3](#solution3)
- `age()` method declared in `class User {}` is still going to added to the prototype like at [solution 3](#solution3).

> Using the class syntax is the standard, but it's important to know other means in order to debug code efficiently.

So the proper way of achieving our goals since the beginning of this article is by using the `class` syntax - solution 4.

## Conclusion

All the techniques we've covered are aimed at achieving a better way of storing data (properties) and functionalities (method) together in one place which can be used multiple times as need. Also, is the technique easy to reason about, could new functionalities (methods) be added easily and finally is the technique efficient and performant? 

That's for you to ponder about...

---

Here is a video I highly recommend, it covers these concepts further and it's by [Ifeoma Imoh](https://www.youtube.com/channel/UCxPaN6CXAGX1NNa-2ATU5bg) 

%[https://youtu.be/Pl926lQME2c]


Other articles to read on further include:

- [Understanding JavaScript Prototype](https://hashnode.com/post/understanding-javascript-prototype-ckh46aiwv036r39s1a5pe5ec4) by @[Zell Liew](@zellwk)
- [A conversation with the 'this' keyword in Javascript](https://dev.to/developerkaren/a-conversation-with-the-this-keyword-in-javascript-3j6g) by @[Efereyan Karen Simisola](@Karen5)
- [Execution Context and Call Stack](https://favouritejome.hashnode.dev/execution-context-and-call-stack)
- [Callback Functions and Higher Order Functions](https://favouritejome.hashnode.dev/callback-functions-and-higher-order-functions)

I know it's been a lot, and I hope you've learnt one or two things, **Thanks for Reading**.
