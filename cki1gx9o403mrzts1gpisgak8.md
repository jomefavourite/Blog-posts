---
title: "Practising React"
datePublished: Sat Nov 28 2020 09:04:15 GMT+0000 (Coordinated Universal Time)
cuid: cki1gx9o403mrzts1gpisgak8
slug: practising-react
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1606553295609/4m4yu78Cm.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1606553301798/8VXtG_goP.png
tags: javascript, reactjs, hashnodebootcamp

---

Hello, everyone 👋. So this is a task from @[Anna J McDougall](@AnnaJMcDougall) at Hashnode Bootcamp where she talks about "Getting Started in Blogging".

**Task**: In 7 days, write a blog post from one of the topics.

There were 6 topics but for this article, I'll write about one of the topics **"Technology itself".**

This article is all about a problem I encountered while practising React and how the problem got fixed.

---

I recently started learning React and I've been trying to come up with ideas to practice the little have learnt so far. Then, I came across a project by [Mercy Amah](https://twitter.com/Mercyoncode) where she made a multiplication table generator then I thought to myself, can I implement the same concept of the multiplication table generator using React?

I gave it a go and I did make it work sort of. But there was an issue whereby the output is dependents on the input value and that's not how [Mercy Amah](https://twitter.com/Mercyoncode) made hers. I tried as much to make it work as much as I could but failed, so I decided to ask the tech community on Twitter. Luckily I got a response from @[JCLee](@ljc_dev).

Here's Mercy [demo](https://amahmercy123.github.io/multiplication-table/)

My code: 

```js
import React, {useState} from "react";

const Multiplication = () => {
  let [multiplier, setMultiplier] = useState("");
  let [range, setRange] = useState("");
  let [click, setClick] = useState(false);

  let output = [];
  for (let i = 1; i <= range; i++) {
    output.push(`${multiplier} x ${i} = ${multiplier * i} `);
  }

  return (
    <div>
      <div>
        <div>
          <h4>Multiplier</h4>
          <input
            value={multiplier}
            type='number'
            onChange={e => setMultiplier(e.target.value)}
          />
        </div>
        <div>
          <h4>Range</h4>
          <input
            value={range}
            type='number'
            onChange={e => setRange(e.target.value)}
          />
        </div>

        <div>
          <button
            style={{marginTop: 20}}
            onClick={() => {
              multiplier.length > 0 && range.length > 0
                ? setClick(true)
                : setClick(false);
            }}
          >
            Generate Result
          </button>
        </div>
      </div>

      <div>
        <h4>Output</h4>
        {click && output.map((item, i) => <p key={i}>{item}</p>)}
        {console.log(click)}
      </div>
    </div>
  );
};

export default Multiplication;
```
View the sandbox [here](https://codesandbox.io/s/multiplication-table-lvx51) to play around with the code.

The issue I had was that the output was dependent on the values in the input so as soon as I clear the inputted value the output changes also I wasn't able to make the button active. I mean so that when it's clicked then should the output be displayed.


![Screenshot (260).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606553810225/Oo1WmPflc.png)


![Screenshot (261).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606553822428/ZjXkyEevz.png)

I knew I was to store the result (output from multiplication) in a variable then is get displayed and then not dependent on input just like the demo by Mercy.

**Solution by JC :**
```js
import React, { useState } from "react";

const Multiplication = () => {
  let [multipler, setMultipler] = useState("");
  let [range, setRange] = useState("");
  let [table, setTable] = useState([]);

  function getTable(){
  let output = [];
  for (let i = 1; i <= range; i++) {
    output.push(`${multipler} x ${i} = ${multipler * i} `);
  }
  return output.map((item, i) => <p key={i}>{item}</p>)
  }

  return (
    <div>
      <div>
        <div>
          <h4>Multipler</h4>
          <input
            value={multipler}
            type="number"
            onChange={(e) => setMultipler(e.target.value)}
          />
        </div>
        <div>
          <h4>Range</h4>
          <input
            value={range}
            type="number"
            onChange={(e) => setRange(e.target.value)}
          />
        </div>

        <div>
          <button
            style={{ marginTop: 20 }}
            onClick={() => {
              if(multipler.length > 0 && range.length > 0){
                setTable(getTable())
              }
            }}
          >
            Generate Result
          </button>
        </div>
      </div>

      <div>
        <h4>Output</h4>
        {table}
      </div>
    </div>
  );
};

export default Multiplication;

``` 

JC added `let [table, setTable] = useState([]);` whereby there are two variables:`table` which holds the value of an empty array and `setTable` which updates the table later on.

Also `getTable()` function wraps all my logic so that when the button element is clicked the function will be invoked.

```js
 <button
      style={{ marginTop: 20 }}
      onClick={() => {
        if(multipler.length > 0 && range.length > 0){
            setTable(getTable())
        }
      }}
 >
     Generate Result
</button>
```

By adding the function invocation in the `if` condition which then invokes the `getTable()` function if the condition is met and then derives the desired result which I wanted. The returned array `output.map((item, i) => <p key={i}>{item}</p>` is then fixed into `table` variable. So this makes the result show even though there's nothing at the input whereby the result is based on the input values once the button has been clicked.

![Screenshot (263).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606553920761/cNuW6_h2O.png)

So my goal with this article is to learn how to ask for help when needed. As a code newbie like myself, this is very important to learning faster.

### Conclution

This task had some specific instructions which are:

- Structure < 300 words.
- No “you”, only “us” and “we.
- As little passive voice as possible.
- Try to use three words you didn’t know before.

Sadly I've not able to meet the 2-4 requirements and I didn't write this blog for seven consecutive days. Schools have been stressful because we are about to go home for holidays and we are to be given a series of test assessment so I'.m struggling to make ends meet. 

But I do remember the points Anna pointed out and I'll try to abide by them in my upcoming articles. 

**Thanks for reading** 



