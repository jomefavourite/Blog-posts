---
title: "Several Ways of Positioning Elements to the Center using  CSS"
datePublished: Mon Dec 07 2020 08:58:25 GMT+0000 (Coordinated Universal Time)
cuid: ckiebof4w06gv6zs1htsb8u0q
slug: several-ways-of-positioning-elements-to-the-center-using-css
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1607275043414/UbO9GxTJd.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1607275047738/xGoAykq0-.gif
tags: css, web-design, html5, beginners, hashnodebootcamp2-1

---

Hello! 👋 So a while back, when I was starting my learning journey with HTML and CSS, I found it very difficult to center elements on the web page either vertically or horizontally and since this is a big issue for me, I decided to make a video on my [YouTube channel](https://www.youtube.com/watch?v=RZzQES7Z6m8) about it where I showed how to position element centrally both vertically and horizontally.

This article is not based on the video, because I noticed I left out somethings on how to achieve the goal of centering elements. So here are my current tips on how to achieve this goal.

Before the tips, I like to make it clear. Elements can be positioned both vertically and horizontally, elements could also be positioned diagonally but for this article, we'll look at both the horizontal and vertical way.

---

## Horizontal methods

### Text - Center 
As you may already know, `text-align: center` is the most basic way of positioning text horizontally, so there isn't much here 😊.

```
.element__with__text {
  text-align: center;
}
```

### Margin
Using the margin property also center's an element horizontally but note only **block elements.**

```css
.element__selector {
    margin: 0 auto;
}
```
From the above example, I'm using a shorthand method of writing CSS, where `0` represent both `margin-top` and `margin-bottom`. Meanwhile `auto` represent both `margin-left` and `margin-right`.

So, it could also be written like this:

```css
.element__selector {
    margin-left: auto;
    margin-right: auto;
}
```
Now, what's `auto` value all about? You may wonder. 

It simply takes the available horizontal space in the element’s container equally – and makes the element get centered.

> Images can also be centered using this method when the image is changed to a block element (`display: block`) but by default images are inline-element.

%[https://codepen.io/jome-favourite/pen/PoGZXzv]

### Transform - left <span id="transformleft"></span>

Using the transform property is also another way to horizontally center. But there must be a parent selector where the child selector is nested, so it's the child selector that'll be horizontally centered.

__Example: __

```html
<!-- .html -->

<div class="parent">
    <div class="child"></div>
</div>
```

```css
/* .css */

.parent {
  position: relative;
  width: 100%;
}

.parent .child {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}
```

From the example above, making the `.parent` selector relatively positioned (`position: relative`), allows it to contain the absolutely positioned element - `.child` selector.

Meanwhile, the child selector has the position property value set to absolute `position: absolute` which allows `top`, `right`, `bottom`, `left` properties to be active.

Notice on the child selector `.child` there is a property `left` having the value `50%` which means the child selector is to take 50% of the width of the `.parent` selector which is `100%`.

> `left: 50%` doesn't make the element centered instead makes the starting point of the element move the center of the parent element. Example below

%[https://codepen.io/jome-favourite/pen/OJRMrXe]

Using `transform` property set value to `translateX(-50%)` moves the element to it centered position on it width.

> Note: **X** in the value `translateX` means x-axis which is left or right positions.

**Example:**
 
%[https://codepen.io/jome-favourite/pen/KKgVbZN]

### Flex - justify-content

Using the flex container property `justify-content` is also a way of positioning all child elements (flex items) of the parent element to the center horizontally.

**Example:**

```css
.flex-container {
   display: flex;
   justify-content: center;
}
```

### Grid - justify-content

Giving the `display` property value `grid` also has the `justify-content` property which does the same job as flex `justify-content` property,  but for it to work we'll have to introduce a special grid property which only belongs to grid containers which is `grid-template-columns`.

`grid-template-columns` assigns the width to each `.grid-item` and also determines how many columns should be created. If you'll like to read more about **grid** click [here](https://www.w3schools.com/css/css_grid.asp).

> Note: the number of `.grid-item` determines how the `.grid-container` is filled.

```html
<!-- .html -->

<div class="grid-container">
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
</div>
```

```css
/* .css */

.grid-container {
  display: grid;
  justify-content: center;
  grid-template-columns: 50px 50px 50px; 
}
```
%[https://codepen.io/jome-favourite/pen/MWjyyNZ]

---

## Vertical methods

### Transform - top

This is still similar to [transform - left](#transformleft), the only difference is that the `.child` selector uses the `top` property and `transform` property is to the `Y` - axis.

Literally, the same concept as [transform - left](#transformleft).

__Example:__

```html
<!-- .html -->

<div class="parent">
    <div class="child"></div>
</div>
```

```css
.parent {
  position: relative;
  width: 100%;
}

.parent .child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%)
}
```

### Flex - align-items

Using the `align-items` property on the flex-parent selector aligns all the child element vertical. An example is the best way to illustrate my point :

```html
<!-- .html -->

<div class="flex-container">
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
  <div class="flex-item"></div>
</div>
```

```css
/* .css */

.flex-container {
  display: flex;
  align-items: center;
}

.flex-item {
  width: 80px;
  height: 100px;
  background: blue;
}
```

%[https://codepen.io/jome-favourite/pen/abmNNjr]

### Grid - align-content

```html
<!-- .html -->

<div class="grid-container">
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
  <div class="grid-item"></div>
</div>
```

```css
.grid-container {
  display: grid;
  align-content: center;
  grid-template-columns: auto auto auto;
}
```

%[https://codepen.io/jome-favourite/pen/dypMMBM]

---

## Centering Vertically and Horizontally

Now, that we've seen both the vertical and horizontal centering, let's look into both together.

### Transform - top, left

Let's look at the __example__ below 

```html
<!-- .html -->

<div class="parent">
  <div class="child"></div>
</div>
```

```css
/* .css */

.parent {
  position: relative;
  width: 100%;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

From the example above, it looks similar to the previous examples on transform above but this time, the `.child` selector has both `top` and `left` property which has the value of `50%`. 

As mentioned before, using only the `top` and `left` property wouldn't center the `.child` element the way it should be, then the `transform` property comes into play.

`transform: translate(-50%, -50%)` is the same as:

```css
transformX(-50%)
tranformY(-50%)
```

Which makes the `.child` element centered as we'll like.

%[https://codepen.io/jome-favourite/pen/poEybgq]

### Flex - justify-centent, align-items

By using the `justify-content: center` (horizontally) and `align-items: center` (vertically) in the flex container or the parent container where `display: flex` is declared, the flexed item will be perfectly centered at both axis. 

__Example:__

```html
<div class="flex-container">
  <div class="flex-item"></div>
</div>
```

```css
.flex-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

%[https://codepen.io/jome-favourite/pen/yLaOJJw]

### Grid - place-content

Using grid `place-content` property, does the job easily. That'll be `place-content: center` which places the grid item to the center (horizontally and vertically) of the given width of the `grid-container`.

__Example:__

```html
<div class="grid-container">
  <div class="grid-item"></div>
</div>
```

```css
.grid-container {
  display: grid;
  place-content: center;
}
```

%[https://codepen.io/jome-favourite/pen/xxEVORZ]

## Conclusion

You should be very careful though while centering elements around the web page, it could result in some unexpected outcomes especially using `transform` property.

Hopefully, you've learnt something, if you have any question please do comment below. **Thanks for reading** 😊.

