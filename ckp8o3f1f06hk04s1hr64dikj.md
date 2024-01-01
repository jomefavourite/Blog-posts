---
title: "The World of Programming Paradigms"
seoTitle: "The World of Programming Paradigms - Favourite Jome"
seoDescription: "Programming Paradigm can be thought of like a way/style of writing programs. Also, it can be viewed as ways programs are classified based on their features."
datePublished: Fri May 28 2021 18:37:19 GMT+0000 (Coordinated Universal Time)
cuid: ckp8o3f1f06hk04s1hr64dikj
slug: the-world-of-programming-paradigms
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1622226774130/DonY-8vzQ.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1622226860453/GcB6FzBOJV.png
tags: programming, programming-languages, programming-tips

---

There are so many ways of writing programs, either by the programming language of choice or by the different features of a language. Understanding this fact will help you write more efficient programs if you ask me 😏.

So, in this article, I'll be sharing what are programming paradigms and mentioning a few of the paradigms we have out there in the world of programming and also reasons to use a particle paradigm.

---

"The world of programming paradigms" - From the statement, the words can be broken down into three, which are _"World"_, _"Programming"_ and _"Paradigms"_.

Let's know what these words mean:

- **World**: can be thought of as a pictural view of the region/domain. 
- **Programming**: From the word programming, there's another word - program, so what's a program.
<br><br>
A **program** is a set of instructions used to solve/perform a specific task/problem. 
<br><br>
With the word program being defined, now what's programming?
<br><br>
**Programming** is simply the act of writing programs.

- **Paradigms**: are a set of concepts, thought patterns used in a domain/field.

## Programming Paradigms 

So, **Programming Paradigm** can be thought of like a way/style of writing programs. Also, it can be viewed as ways programs are classified based on their features.

There are so many programming paradigms out there, developed to solve problems and implemented in all programming languages like Java, C, JavaScript, etc. Due to the numerous paradigms, we are looking at just the two most common paradigms in this article.

> Note: Programming Paradigms doesn't refer to a particular programming language but rather the way of writing programs in that programming language.

> Click here to view most of the [Programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm) that exist.

Before proceeding further, you should know that mostly all recently used programming languages are multi-paradigm, meaning they can be written using not just one but as many paradigms supported in the language.

There are two common programming paradigms, which are:
- __Imperative programming paradigm__
- __Declarative programming paradigm__

Both programming paradigms can further be divided as shown in the image below:

![programming paradigms](https://cdn.hashnode.com/res/hashnode/image/upload/v1621524352354/hzvq76G5Y.png)

> Note: There're more subdivisions to the Imperative programming paradigm and the Declarative programming paradigm, but we'll be concerned about the subdivisions shown in the image for this article.

### Imperative Programming Paradigm

Firstly, what's the meaning of the word, Imperative?

Imperative could mean something vitally important, crucial or an act of giving an authoritative command.

So, therefore, In an Imperative Programming Paradigm, the order of steps is crucial, because the next step is mostly dependent on the previous step.

Here's an example in JavaScript to demonstrate my point:

```js
let sum = 0

sum+= 1 // sum = sum + 1
sum+= 2 // sum = sum + 2
sum+= 3 // sum = sum + 3

console.log(sum) // 6
```

From the snippet above, we notice that the variable `sum` is initialised with the value `0`. 

Then the next couple of line is dependent on the current value of the variable `sum` which sums up to `6`.

From Imperative Programming Paradigm, other styles of writing programs were also derived and for this article, we'll be looking at two sub-modules which are **Procedural programming** and **Object-Oriented programming**

### Procedural Programming 

Procedural programming is derived from the **Imperative Programming Paradigm**, which allows splitting of instructions into procedures also is concerned about the series of instructions to concur whereby each step relies on the previous step.

Procedural programming is much more like an iterative approach to solving a task/problem using loops (`for`, `while`) and `if` statements for control flow.

Here's an example to find the sum of numbers from 0 to 10, written in JavaScript:

```js
let sum = 0

for (let i = 0; i <= 10; i++) {
  sum+= i 
}

console.log(sum) // 55
```

From the snippet of code above, a `for` loop that iterates from 0 to 10 adding the previous `sum` variable with `i` and then the final output of the variable `sum` will be `55`.

Some major procedural programming language includes Fortran, ALGOL, BASIC and Pascal but more examples are found here [List of programming languages by type - Procedural languages](https://en.wikipedia.org/wiki/List_of_programming_languages_by_type#Procedural_languages)

> [Click here to know more about Procedural Programming](https://en.wikipedia.org/wiki/Procedural_programming)

#### Why learn Procedural Programming?

- It's simple.
- An easier way to keep track of program flow.
- It has the ability to be strongly modular or structured.
- Needs less memory: It's efficient and effective.

### Object-Oriented Programming (OOP)

In Object-Oriented Programming, the concept of classes and objects are used. The paradigms specialise in modularity, breaking real-world entities into objects that can be reused.

Also, Object-Oriented Programming is based on the concept of objects where an object contains data/fields (attributes) and methods (behaviours).

Some key characteristics of the OOP are:

- **Class**: A class is a blueprint or template of an object.
- **Object**: An object is an instantiation of a class.
- **Abstraction**: This is the process of hiding away complexity and showing only what is need.
- **Inheritance**: enables hierarchical relationships between classes.
- **Encapsulation**: is the concept that binds together the data
and methods that manipulate the data, and that keeps both safe from outside
interference and misuse.
- **Polymorphism**: this is the process by which variables, methods or objects can take multiple forms.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

class Student extends Person {
  constructor(name, age, matricNo, level) {
    super(name, age)
    
    this.matricNo = matricNo;
    this.level = level;
  }
  
  getStudenDetails() {
    return `${this.name} is of age ${this.age}, 
his Matric Number is ${this.matricNo} and his in ${this.level}L`
  }
}

const student1 = new Student('Favourite', 18, 'RUN/CMP/18/7796', 300)
console.log(student1.getStudenDetails())

// outputs
// 'Favourite is of age 18, his Matric Number is RUN/CMP/18/7796 and his in 300L'

```

From the snippet of code above, a class `Person` was first declared with its data/attributes as `name` and `age`. Also, the `Person` class is known as the Superclass because another class extends its properties.

Next off, another class was declared as `Student`, this class extends all the properties of the `Person` class because all students are also a person and this brings about inheritance.

#### Why use/learn Database programming

- Reuse of code through Inheritance.
- Flexibility through Polymorphism.
- High security with the use of data hiding (Encapsulation) and Abstraction mechanisms.
- An object-oriented programmer can stitch new software objects to make completely new programs.
- For faster development of programs.

## Declarative Programming Paradigm

Declarative programming is a style of building programs that express the logic of a computation without talking about its control flow.

From the word, **Declarative**; it means an announcement / a statement, so in this paradigm, the instructions that are to be carried out are declared meaning it doesn't need to be explicitly defined with how the instruction is to be meant done but just what is meant to be done.

Imagine being asked to draw a rectangle on a book, an imperative approach would state the various procedures like drawing two parallel lines on both axes while a declarative approach would just state the end goal and doesn't care about the process takes.

So the main differences are that imperative tells you **how to do something** and declarative tells you **what to do**.

Declarative Programming also has some programming languages beneath it, we'll be looking at **Functional Programming** and **Database Programming**.

### Functional Programming

The functional programming paradigm is rooted in using mathematical operation, it's a way of writing programs elegantly like you'll think of when thinking about a problem.

Also, Functional programming is the process of solving problems by composing pure functions, avoiding shared state, mutable data, and side effects. Functional programming is declarative rather than imperative, and application state flows through pure functions

Terms like: Recursion, Memoization, Pure Function, Composition are used along with  Functional Programming. 

Let's say, a Fibonacci problem is to be solved, using a Functional approach makes the problem easier to solve and think about.

> Each Fibonacci number is defined as the sum of the previous two Fibonacci numbers, so fibonacci(n) = fibonacci(n-1) + fibonacci(n-2). By convention, the first two numbers are fixed: fibonacci(0) = 0 and fibonacci(1) = 1.
 
Here's the Functional approach of solving a Fibonacci problem using JavaScript.
```js
function recursiveFibonacci(n) {
  if ( n <== 0) return 0
  if ( n === 1) return 1
  
  return recursiveFibonacci(n-1) + recursiveFibonacci(n-2)
}

recursiveFibonacci(6) // 8
```

> Note, there some caveat to Functional Programmings, like the Memory Stackoverflow, but there are also solutions to this caveat like [Tail Call Optimation](https://youtu.be/-PX0BV9hGZY)

Read this wonder article to know more about Functional Programming: [Master the JavaScript Interview: What is Functional Programming?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0#:~:text=Functional%20programming%20(often%20abbreviated%20FP,state%20flows%20through%20pure%20functions.)

#### Why use/learning Functional programming?

- Functions can be coded quickly and easily.
- Unit testing is easier.
- Debugging is easier.
- Overall application is less complex since functions are pretty straightforward.

### Database Programming

A database is an organized collection of structured information, or data,
typically stored electronically in a computer system. A database is usually
controlled by a database management system (DBMS).

To process the data and querying them, databases use tables. Data can then be
easily accessed, managed, modified, updated, controlled and organized.

Most databases use Structured Query Language (SQL) for writing and querying
data.

There're three major parts to Database Programming: 
- Relational Database
- NoSQL Database
- Cloud Database

> Read this article to know more about Databases: [What is a Database? - edureka](https://www.edureka.co/blog/what-is-a-database/)

Below, are simple declaration and schema declaration on what should be in a data show be in a database.

```sql
CREATE DATABASE Students;

CREATE TABLE ComputerScienceStudent (
      MatricID int,
      LastName varchar(25),
      FirstName varchar(25)
);
```

#### Why learn/use Database Programming

- When you need to handle massive amount of data.
- With the help of built-in functionalities in a database, we can easily validate data coming into the database.
- Easy to update data: Data Manipulation Languages (DML) such as SQL are used to
update data in a database easily.
- Data integrity: With the help of built-in validity checks, we can ensure the consistency of data.

## Conclusion

I'm pretty sure in some ways, directly or indirectly you've written programs using the combinations of all the Programming paradigms mentioned above, probably without your knowledge. Well, know you know some of the most used programming paradigms and reasons to use them.

I hope you found the article useful, thanks for reading!

## References
- [What exactly is a programming paradigm? - Freecodecamp](https://www.freecodecamp.org/news/what-exactly-is-a-programming-paradigm/)
- [List of programming languages by type - Wikipedia](https://en.wikipedia.org/wiki/List_of_programming_languages_by_type)
- [Programming Paradigms: A must know for all Programmers - hackr.io](https://hackr.io/blog/programming-paradigms)
- [Programming paradigms - java-programming.mooc.fi](https://java-programming.mooc.fi/part-7/1-programming-paradigms)
- [What is a Database? Definition, Types and Components](https://www.edureka.co/blog/what-is-a-database/)























