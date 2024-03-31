---
title: "Tailwind CSS just got better!"
seoTitle: "Tailwind CSS just got better!"
seoDescription: "Tailwind CSS recently launched some awesome updates in v3.4, supporting CSS features like Dynamic viewport units, has pseudo class"
datePublished: Sun Mar 31 2024 22:19:01 GMT+0000 (Coordinated Universal Time)
cuid: clug32qqa000008jm9lk0font
slug: tailwind-css-just-got-better
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711923463206/56e95848-606b-40e5-abdd-0c1c69d382ab.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1711923480699/51d29392-e7b6-48d5-b4fb-51d98433f519.png
tags: tailwind-css

---

Tailwind CSS recently launched some awesome updates in v3.4, supporting CSS features like Dynamic viewport units, subgrid supports and other features, which we'll go over in this article.

It's so easy to be carried away by using the already-known features a tool provides without bothering to know the newly added features, in this case, Tailwind CSS. As a Tailwind CSS fanboy myself, I barely try out the new updates happening in CSS since I mainly use Tailwind; however, when those new updates get to TailwindCSS, it's a game-changer since I can now easily make use of them.

## **Dynamic viewport units**

Making a full-height viewport on mobile devices with the `vh` unit wasn't the best because the mobile browser's toolbar usually gets in the way of the viewport, allowing the layout to bleed out. Illustrated below:

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711917443289/ed072f16-7483-4cb5-bf8e-b143a97ffec4.png align="center")](https://web.dev/blog/viewport-units#the-need-for-new-viewport-units)

> Source: [https://web.dev/blog/viewport-units#the-need-for-new-viewport-units](https://web.dev/blog/viewport-units#the-need-for-new-viewport-units)

However, when the viewport is scrolled down, the `vh` unit works as expected cause now the browser's toolbar is retracted.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711917688457/382105bc-169f-4f9b-bdc3-da37ace075ab.png align="center")

> Source: [https://web.dev/blog/viewport-units#the-need-for-new-viewport-units](https://web.dev/blog/viewport-units#the-need-for-new-viewport-units)

To combat this issue, new viewport units were added to CSS, namely Large viewport, Small viewport and Dynamic viewport, having the prefix `lv`, `sv`, `dv` respectively. Dynamic viewport units are essentially the combination of both small and large viewport units.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711918931569/a89c173d-8ff4-44b3-bd60-f20d5e4c70c7.png align="center")

> Source: [https://web.dev/blog/viewport-units](https://web.dev/blog/viewport-units)

Here are some dynamic viewport units added to Tailwind CSS by default `w-svw`, `w-lvw`, `w-dvw`, `h-svh`, `h-lvh`, `h-dvh` and arbitrary values like this `min-h-[75dvh]` works as well 🤩.

# :has() pseudo-class

The `:has()` pseudo-class is one of those cool features recently added to CSS that I haven't got to play a lot with; since it's now supported in Tailwind CSS, it just opens a new world of possibilities 🤯.

*The*[`:has()`*pseudo-class*](https://developer.mozilla.org/en-US/docs/Web/CSS/:has) *allows you to style an element based on its children, not just based on its parents. It even makes it possible to style based on subsequent siblings - From the* [*Tailwind CSS blog*](https://play.tailwindcss.com/yuQyHjiuSx)

Essentially, think of the `:has()` pseudo-class as a shortcut and a better way to do some crazy things you might have done with SASS or JavaScript but now can be done with plain CSS or, in this case, Tailwind CSS 🤩

Here's a silly example to illustrate how the `:has()` pseudo-class work, in this case, if the child element (`img`) is next to a paragraph then the background of the parent element changes to red.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711922504420/969f1f1b-abee-4dc0-ba81-b81eab6032fc.png align="center")

```xml
<div class="has-[img+p]:bg-red-400">
   <div class="p-4">
     <img src="..." alt="">
   </div>
   <div class="p-4">
     <img src="..." alt="">
     <p>This is a paragraph</p>
   </div>
</div>
```

> Preview code example here: [https://play.tailwindcss.com/FDBP3zqjoS](https://play.tailwindcss.com/FDBP3zqjoS)

> Here's a guide showing ten practical examples that utilizes the CSS :has selector: [https://bejamas.io/blog/learn-css-has-selector-by-examples-top-use-cases/](https://bejamas.io/blog/learn-css-has-selector-by-examples-top-use-cases/)

## The \* variant

The \* variant is a blessing from Tailwind CSS, allowing us to now style children's elements from the parent using utility classes. Here's a code example and preview of how it works:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711921397770/ab1d69d8-1ee2-4917-825b-88308dd520b4.png align="center")

```xml
<div>
  <h2>Categories:<h2>
  <ul class="*:rounded-full *:border *:border-sky-100 *:bg-sky-50 *:px-2 *:py-0.5 dark:text-sky-300 dark:*:border-sky-500/15 dark:*:bg-sky-500/10 ...">
    <li>Sales</li>
    <li>Marketing</li>
    <li>SEO</li>
    <!-- ... -->
  </ul>
</div>
```

> Preview code example here: [https://play.tailwindcss.com/yuQyHjiuSx](https://play.tailwindcss.com/yuQyHjiuSx)

## The size-\* utilities

The `size-*` utilities allow you to set the width and height at the same time, which is very useful when working with icons or avatars.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711920173529/9bc51c73-7891-440b-b37f-4eabf4cfce9a.png align="center")

```xml
<div class="flex gap-6 items-end">
  <img class="size-14 rounded-full" src="https://avatars">
  <img class="size-20 rounded-full" src="https://avatars">
  <img class="size-24 rounded-full" src="https://avatars">
</div>
```

> Preview code example here: [https://play.tailwindcss.com/NawRNldMH4](https://play.tailwindcss.com/NawRNldMH4)

---

Well, that rounds it up for the newly added exciting features in Tailwind CSS, there are a bunch of other cool updates that came with v3.4, do check out the [blog announcement](https://tailwindcss.com/blog/tailwindcss-v3-4).

To get started with these new features, upgrade your projects by installing the latest version of `tailwindcss` from npm:

```bash
$ npm install tailwindcss@latest
```

## References

* [Web.dev - The large, small, and dynamic viewport units](https://web.dev/blog/viewport-units)
    
* [New CSS Viewport Units Do Not Solve The Classic Scrollbar Problem](https://www.smashingmagazine.com/2023/12/new-css-viewport-units-not-solve-classic-scrollbar-problem/)
    
* [TailwindCSS](https://tailwindcss.com/)