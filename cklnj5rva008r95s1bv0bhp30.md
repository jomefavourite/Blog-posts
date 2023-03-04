---
title: "Understanding Pass by Value and Pass by Reference"
seoTitle: "Understanding Pass by Value and Pass by Reference - Favourite Jome"
datePublished: Sat Feb 27 2021 09:36:54 GMT+0000 (Coordinated Universal Time)
cuid: cklnj5rva008r95s1bv0bhp30
slug: understanding-pass-by-value-and-pass-by-reference
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1614303747230/mZbeN12Mb.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1614303861742/QN7V1o79w.jpeg
tags: javascript, reactjs, programing

---

The concept Pass by Value and Pass by Reference is one I ignored while learning vanilla JS, so when I was faced with a challenge I couldn't wrap my head around the concept. So in this article, I'll be giving instances to these concepts so as for us to grasp the basics of the concept once and for all.

## What's Pass by Value?

Pass by Value is majorly used with primitive types (data types) such as:

* String
    
* Number
    
* Boolean
    
* Undefined
    
* Null
    

Simply, **Pass by Value** is when a value from a variable with a primitive data type is **copied** with the `=` sign into another variable. Hence, the value of a primitive type is also known as a primitive value.

Here are instances of the five primitive types following the concept Pass by Value

```js
// String
let name = "Favourite";
let newName = name;

// newName = "Favourite"

//Number
let count = 50;
let age = count;

// age = 50

// Boolean
let isNew = true
let isFeatured = isNew

// isFeatured = true

// Undefinded
let isUndefined;
let empty = isUndefined

// empty = undefined

// Null
let isNull = null
let isAlsoNull = isNull

// isAlsoNull = null
```

> I know, I know, these are basic stuff in JS but did you know that the concept was called Pass by Value? Well if you did, Kudos to you if not, now you know 😀.

With Pass by Value, the variable copied is clearly the same as the initial variable copied from, so what if the copied variable is changed?

Example:

```js
// String
let name = "Favourite";
let newName = name;

newName = "Success";

// name = "Favourite"
// newName = "Success"
```

Let's go through the example line by line,

* A variable is declared as `name` which has a value `"Favourite"` stored in memory and can only be addressed by the variable name `name`.
    
* Another variable is declared as `newName` with the value `name` which is a variable and equivalent to the value `"Favourite"`. So `newName = "Favourite"` stored in memory and now addressable by the variable name `newName`.
    
* > At this point, both variable `name` and `newName` has the same value but they are addressed differently with there unique variable names.
    
* Variable `newName` changes it's value to `"Success"`. Therefore, the memory space for `newName` contains the new value `"Success"`.
    

> If you're unclear about what the term memory means, you can read this article [Principles of Javascript](https://favouritejome.hashnode.dev/principles-of-javascript) where I discussed the term memory.

At this point, we have different values initialised in both variables `name` and `newName`, notice that `name` still has the value `"Favourite"` even though it was copied and then changed by the variable `newName`.

> So, therefore, **Pass by Value** is when a variable value is copied into another variable as a value, without both variables referencing the same value even though the value might be the same. So if one of the variables change it value, there's no connection or link to the other variable.

That's pretty much all on the concept Pass by Value.

## What's Pass by Reference

Pass by Reference is majorly used with non-primitives types, such as

* Object
    
* Array
    

> Note: Arrays are a special type of Object

### Object

When a value from a variable which is a non-primitive data type is **copied** with the `=` sign into another variable, the address of that value is what’s actually copied over as if it were a primitive type.  
Objects are copied by reference instead of by value.

**Example:**

```js
let obj1 = {
  item1 : "Books",
  item2: "Pens"
};
let obj2 = obj1;

obj2.item1 = "Pencil"

console.log(obj1)
// {item1: "Pencil", item2: "Pens"};
console.log(obj2)
// {item1: "Pencil", item2: "Pens"};
```

From the example above, both `obj1` and `obj2` have the same output when logged to the console, so the big question is why right?

**Why**

This is because when an object is assigned to a variable, the variable holds the address location of the object in memory and not the object itself. Thereby, the variable references the object through the address location in memory.

Hmm, the reason might seem daunting, so here is an illustration to help.

![Learning (4).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1614302928092/SU2mVaVg6.png align="left")

Let's go over the above [example](#objexp) line by line:

* A variable named `obj1` is declared initialized with an object as its value.
    
    * At this point the object `{item1: "Books", item2: "Pens"}` is stored somewhere in memory having an address to where it's stored. Let's denote the address with this symbol `<x>`.
        
    * Then the variable `obj1` holds the address `<x>` to the object instead of the object value itself even though you can clearly see the object.  
        

> All these processes happen at the JS engine.

* Another variable is declared `obj2` initialized with `obj1` as a reference.
    
    * Since variable `obj1` equals `<x>` (which is the address location to the object `{item1: "Books", item2: "Pens"}`), then variable `obj2` equals to the same address location `<x>` which is linked to the object `{item1: "Books", item2: "Pens"}`.
        
* This expression `obj2.item1 = "Pencil"` simply means change the `item1` property value to `"Pencil"` instead of `"Books"`.
    
    * At this point, the variable `obj2` has changed the value to `{item1: "Pencil", item2: "Pens"}` but the address which is actually stored in the variable hasn't changed `<x>`. Since the address hasn't changed and the variable `obj1` also has the address `<x>` that means both variables `obj1` and `obj2` references the same object which is now `{item1: "Pencil", item2: "Pens"}`.
        

---

### Cloning Objects

Now, that we know objects are Passed by Reference when copied as a value to another variable, so how do we stop this behaviour could be another question you might have.  
Well, there're several ways to clone an object.

* **Object.assign() method**
    

`Object.assign()` is an object method that accepts arguments, where the first argument is the target object and the other arguments/argument is the source object.

**Syntax**: `Object.assign(target, ...sources)`

> Here's an article to read up on `Object.assign()` method in this article:  
> [ES6 object.assign() method with Example](https://hashnode.com/post/es6-objectassign-method-with-example-ck5me354b04ovqps150z8mvf1) by @[Sachin Jaiswal](@codesquery)

Example:

```js
let obj = {
  item1: "Books", 
  item2: "Pens"
}
let cloneObj = Object.assign({}, obj)

obj.item2 = "Pencil"

console.log(obj)
// { item1: 'Books', item2: 'Pencil' }
console.log(cloneObj)
// { item1: 'Books', item2: 'Pens' }
```

* **Spread Operator**
    

The spread operator also referred to as the three dots `...` is majorly used to spread out the content of an iterable i.e string, array, or objects, and thus returns a new variable.

> Here are articles to read up for further understanding:  
> [JAVASCRIPT SPREAD OPERATOR SIMPLIFIED](https://qeescancode.hashnode.dev/javascript-spread-operator-simplified) by @[Balqees Ibrahim](@qeesCanCode)  
> [10 ways to use the spread operator in JavaScript](https://h.daily-dev-tips.com/10-ways-to-use-the-spread-operator-in-javascript) by @[Chris Bongers](@dailydevtips)

Example:

```js
let obj = {
  item1: "Books", 
  item2: "Pens"
}
let cloneObj = {...obj}

obj.item2 = "Pencil"

console.log(obj)
// { item1: 'Books', item2: 'Pencil' }
console.log(cloneObj)
// { item1: 'Books', item2: 'Pens' }
```

> Using both `Object.assign()` method and the spread operator `...` are both **Shallow Cloning.**  
> Read about Shallow Cloning here:  
> [What is Shallow Copy in JavaScript?](https://rahulism.tech/what-is-shallow-copy-in-javascript) by @[Rahul](@RAHULISM)

> Shallow Cloning happens at only the first layer of the object which is cloned.

* **JSON.parse() and JSON.stringify() methods**
    

Making use of `JSON.parse()` and `JSON.stringify()` methods is know as **Deep Cloning**. This is where an object has another object as its property value and you'll like the objects to be cloned.

> Here's an article that covers the topic Deep Cloning:  
> [Deep Copy vs. Shallow Copy in JavaScript](https://charandev.com/deep-copy-vs-shallow-copy-in-javascript) by @[Devalla Sai Charan](@charandev)

```javascript
let obj = {
  item1: "Books", 
  item2: {
    item2_1: "Pens",
    item2_2: "Marker"
  }
}
let cloneObj = JSON.parse(JSON.stringify(obj))

obj.item2.item2_1 = "Pencil"

console.log(obj)
//  { 
//    item1: 'Books', 
//    item2: { 
//       item2_1: 'Pencil',
//       item2_2: 'Marker'
//     }
//  }
console.log(cloneObj)
// { 
//  item1: 'Books', 
//  item2: {
//    item2_1: 'Pens', 
//    item2_2: 'Marker' 
//  }
// }
```

---

Here are more instances of Pass by Reference to test yourself, try guessing the answer and figuring why

```js
// Example 1
function byReference(personObj) {
  personObj.name = "John"
  personObj = {
    name: "Favourite", 
    age: 18
  }

  return personObj
}

const person = {
  name: "Doe",
  age: 20
}

const newPerson = byReference(person);

console.log(person)
console.log(newPerson)

// Example 2
let todos = [
  {id: 1, title: "Read for exam", done: false},
  {id: 2, title: "Complete my article", done: false},
  {id: 3, title: "Apply for Github Campus Expert before 28", done: false}
]

let todo = todos.map(todo => {
  if (todo.id === 1) todo.done = true

  return todo
})

console.log(todo)
console.log(todos)
```

### Array

An array is used to store similar data types and is a special object. Since it an object/special object it also follows the Passed by Reference concept.

Example

```js
let fruits = ["orange", "apple", "mango"]
let newFruits = fruits
newFruits.push("pineapple")

console.log(fruits)
// [ 'orange', 'apple', 'mango', 'pineapple' ]
console.log(newFruits)
// [ 'orange', 'apple', 'mango', 'pineapple' ]
```

From the example above, you'll notice its similar to the [object example](#objexp). Even though it's an array the same approach is carried out.

---

Here's a video made by my friend [Olli](https://twitter.com/R4MSE5), it's all about the concept Pass by Value and Pass by Reference. I'll suggest you watch the video, the visual illustration makes the concept easier to understand if you prefer visual illustrations.

%[https://youtu.be/lAjshs4yLKg] 

## References to read further

* [Explaining Value vs. Reference in Javascript](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)
    
* [ES6 object.assign() method with Example](https://hashnode.com/post/es6-objectassign-method-with-example-ck5me354b04ovqps150z8mvf1)
    
* [JAVASCRIPT SPREAD OPERATOR SIMPLIFIED](https://qeescancode.hashnode.dev/javascript-spread-operator-simplified)
    
* [10 ways to use the spread operator in JavaScript](https://h.daily-dev-tips.com/10-ways-to-use-the-spread-operator-in-javascript)
    
* [Deep Copy vs. Shallow Copy in JavaScript](https://charandev.com/deep-copy-vs-shallow-copy-in-javascript)
    

## Conclusion

Pass by Value and Pass by References are essential concepts one must understand if you'd like to advance your skills using JavaScript. I hope the article was helpful, please do leave comments below, if you have any questions shoot. Thanks for Reading. If you'd like to contact me, you can [here @favouritejome1](https://twitter.com/FavouriteJome1).