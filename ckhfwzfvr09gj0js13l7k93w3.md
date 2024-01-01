---
title: "Tips for making a Responsive Layout"
datePublished: Fri Nov 13 2020 07:02:54 GMT+0000 (Coordinated Universal Time)
cuid: ckhfwzfvr09gj0js13l7k93w3
slug: tips-for-making-a-responsive-layout
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1605138903253/HVdokZTg2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1605138894962/8acWmQ3dZ.png
tags: css, tips, responsive-web-design, hashnodebootcamp, hashnodebootcamp2-1

---

Hello everyone 👋, in this article I'll be sharing what I have learnt on how to tackle responsive layout. 

This article is a task from @[Chris Bongers](@dailydevtips) on Hashnode Bootcamp II technical writing virtual meetup.

The task is to create an article that would help my past self solve a problem I've encountered. Making layout responsive was a problem to me so hopefully these tips helps.

Before diving into the discussion for today, I want you to know by default your plain HTML file viewed on the browser is fully **responsive**. It's you adding CSS rules, images and so on that makes it not responsive so basically you're at fault 😊.

## 1. Use responsive properties

Hmm, what do I mean by responsive properties, you may ask?

Well, this is when you have a general container`<div class="container">` also known as the parent to the child elements, that makes all child element in it responsive to the browser's viewport.

> I choose to call the `<div>` class `.container`. It could be any name though.

```html
<html>
<head>
...
</head>
<body>
  <!-- "container is the responsive tag" -->
  <div class="container">
    <header>
        // other contents / tag maybe here
    </header>
    <main>
        // other contents / tag maybe here
    </main>
    <footer>
        // other contents / tag maybe here
    </footer>
  </div>
</body>
</html>
```

Here's what makes the `div` tag with the class of `container` responsive.

```css
.container {
   width: 80%;
   margin: 0 auto;
   max-width: 400px;
}
```

Note: 
- `width: 80%` means it's taking `80%` width at different viewport from its parent which in this case is the `<body></body>` tag.

- `margin: 0 auto`: the first value `0` is for top and bottom position and `auto` means that the `<div class="container">` tag should be at the centre (left and right) of the viewport.

- `max-width: 400px` this makes `.container` selector stop growing at `400px` width but below `400px` it shrinks based on `80%` width of the viewport.

**P.S**: My example isn't suitable for all layout, so you should be aware of where you'll add the responsive properties and were not too.

Another suitable structure will be :
```
<header class="container"> 
   ...
</header>
<main class="container">
  ...
</main>
<footer class="container">
  ...
</footer>
```

%[https://codepen.io/jome-favourite/pen/YzWRgao]

> Play with the HTML, CSS file to undestand better

## 2. Make use of Max-Width

`max-width` property is very essential when it comes to making a layout feel responsive. 

In a case where you have lengthy words which is stretched out on the browser's viewport, your layout could look messy and feel weird. So it's a better practice to use `max-width` when you want a section of your layouts or stretched words to have an end width meaning it doesn't grow any further than the given width.

Let's look at an example where the text below has a `max-width` and when it doesn't:

%[https://codepen.io/jome-favourite/pen/abZQxzM]

> Please click on the zoom key (`0.5x`, `0.25x`) on the codepen to view my point, and decide which is better. <br>
<br>
Notice I didn't add a fixed width to the `<p></p>` element so by default it's `100%` of the parent container `<div class="section2>`

## 3. Use Box Sizing Property

To be precise you're to use  `border-box` value:
```css
* {
  box-sizing: border-box;
}
```

By default, the browser uses :
```
* {
  box-sizing: content-box;
}
```

Note I'm including this property in the *universal selector* `*`, which select all elements you have in your HTML file and convert the default `content-box` to `border-box`.

So when the browser uses `content-box` here's what happen:

%[https://codepen.io/jome-favourite/pen/LYZMPRW]

> View the HTML and CSS code to see the differences

If you notice the width, height, border and background are shared between `.first` and `.second` selectors. But It's just that the first`<div class=""first>` tag has `padding` added which makes it different from the second element `<div class="second">`.

- `box-sizing: content-box` calculate like this for `.first` selector: 
  - width + border (border left + border right) + padding (padding left + padding right)
  - height + border (border top + border bottom) + padding (padding top + padding bottom)

- `box-sizing: content-box` calculate like this for `.second` selector: 
  - width + border (border left + border right)
  - height + border (border top + border bottom)

```
.first width: 200px + (5px + 5px ) + (50px + 50px) = 310px
      height: 100px +  (5px + 5px) + (50px + 50px) = 210px

.second width: 200px + (5px + 5px) = 210px
        height: 100px +  (5px + 5px) = 110px

```

So what does `box-sizing: border-box` do?

%[https://codepen.io/jome-favourite/pen/QWEzLaX]

- `box-sizing: border-box` calculate like this: 
  - width - border (border left + border right) - padding (padding left + padding right)
  - height - border (border top + border bottom) - padding (padding top + padding bottom)

> Substracts the width or height from other units.

Read this article by @[Edidiong Asikpo](@didicodes) [here](https://edidiongasikpo.com/how-the-css-box-sizing-property-controls-the-size-of-elements) to really grasp the concept. 

Also, you need the knowledge of the box model, you could also read this [article](https://kolosek.hashnode.dev/a-beginners-guide-to-box-model-in-css-ck6rnzojg03fidfs1g2kxl8ci) by @[Nesha Zoric](@kolosek)

## 4. Avoid Heights, fixed width and use Percentages

Why? You may ask. 

Well, it's known that all **Block elements** have a width of `100%` to their parent element. So by given a fixed width to a Block element, let say `500px`. You take away the responsiveness when that block element is viewed on a viewport below `500px` and introduce scroll bars.

Similar issue is created when using a fixed height. 

But using Percentages and padding works wonderfully.

An example will be best to demonstrate the above points.

%[https://codepen.io/jome-favourite/pen/RwRqOjo]

> If you're on a tablet on PC viewport, you won't see the effect of the fixed width, please shrink your viewport to mobile view to see the effect.

## 5. Making Images Responsive

You make an image responsive by including `width: 100%` to its selector in your CSS file.

Doing that will make the image grow depending on the width of the browser's viewport.

%[https://codepen.io/jome-favourite/pen/JjKwPvJ]

Also make images a block element could be used but only if necessary.

> Notice I didn't add `height` property. Using `height` could cause some issues so use it when neccessary.

## 6. Use Relative Units

There are `em`, `rem` and so on, that depends on the browser's width, height or zoom to determine the size of an element.

Using `px` unit will also be fixed and not change irrespective of the width / height of the display screen.

I'll advise you watch this [video](https://www.youtube.com/watch?v=_-aDOAMmDHI) by [Kelvin Powell](https://www.youtube.com/user/KepowOb). He really explains the concept of `em` and `rem`.

## 7. Make use of Mobile Approach

Mobile Approach is when you structure a layout while thinking of how the layout looks like on a mobile screen first before considering a tablet and desktop view.

Doing this, makes you write less media queries and is general a lot easy for you.

Note : Some might say otherwise, well try both ways for your self. 

Here is an [article](https://shaydeecoder.hashnode.dev/responsive-design-strategy) by @[Shaydee Coder](@shaydeecoder). He really dives deep into the two strategies (Mobile first or Desktop first)

## Conclusion

Well that's all I've got. If you adhere to all the tips I mentioned, I'm pretty sure your CSS skills will improve.

It will be bad if I don't mention who taught me all these tips on tackling Responsive layout and that'll be [Kelvin Powell](https://www.youtube.com/user/KepowOb). 

Here's the course: [Conquering Responsive Layouts by Kevin Powell](https://courses.kevinpowell.co/conquering-responsive-layouts).

---

**Thanks for Reading** if you've read so far. You could like, share and comment 😉. Also reach me at Twitter [here](https://twitter.com/FavouriteJome1).

