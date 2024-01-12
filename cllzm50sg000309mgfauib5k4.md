---
title: "Why learn Next.js if I already know React.js?"
seoTitle: "Why learn Next.js if I already know React.js?"
seoDescription: "Next.js is for building large applications, usually applications with multiple pages, with complex functionalities and not just a simple todo app..."
datePublished: Thu Aug 31 2023 20:22:57 GMT+0000 (Coordinated Universal Time)
cuid: cllzm50sg000309mgfauib5k4
slug: why-learn-nextjs-if-i-already-know-reactjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693452955520/593f7cb1-8235-496e-b666-c25c2fa129e9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693452962975/04294aa3-0d0e-499e-b4e8-aed05ddb1fd0.png
tags: reactjs, nextjs

---

As a beginner in the web ecosystem, it could be overwhelming to learn new tools, cause there's just a lot to learn and if you've learned a tool that works why migrate to another, right?

Well, there could be so many reasons and In this article, we'll go over 3 reasons why learning Next.js is the next best thing to do after getting the fundamentals of React.js down.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you're not certain you're ready to learn Next.js yet, watch this video by <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.youtube.com/@PedroTechnologies" style="pointer-events: none">PedroTech</a> - (<a target="_blank" rel="noopener noreferrer nofollow" href="https://youtu.be/wd639F9aKU0?si=RiPUCVVruEAv4ElZ" style="pointer-events: none">What You Need to Know Before Learning NextJS</a>).</div>
</div>

## Prerequisites and Expectation

* Good foundation with React.js
    
* An Introduction to what Next.js offers but not the full gist 😅
    
* Beginner-friendly and assumes the reader doesn't know much about Next.js
    
* Assumes questions a newbie to Next.js might ask.
    

## Introduction to Next.js

Next.js is a React framework for building full-stack web applications [*(referenced from the Next.js documentation)*](https://nextjs.org/docs)*.*

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693439562676/296be42e-8275-4a9b-ac78-54d7dd7f7b64.png align="center")](https://nextjs.org/docs)

Now, you might have questions like:

> What does React framework mean? also,  
> I'm still new to React, I don't want to build full-stack web applications yet 😕

Next.js being a React framework, simply means there are additional features, optimizations and guidelines to follow, that make development easy compared to plain React.js, which's unopionated about routing should be done for example.

As for building **full-stack** web applications, as a newbie you don't need to bother about that, with time and lots of practice, you'll join the train in building full-stack applications.

## Why learn Next.js?

From the introduction of Next.js, I assume you can tell that Next.js is for building large applications, usually applications with multiple pages, with complex functionalities and not just a todo app which is usually everyone's big project learning React.

> Even I built a todo app, some years ago, oh fun memories 😄.
> 
> If you'd like to read about my journey building a todo app which felt like a big project then, here's the article - ([2 months of Learning React.js and The project I worked on](https://favouritejome.hashnode.dev/2-months-of-learning-reactjs-and-the-project-i-worked-on))

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">The reasons below aren't in any particular other</div>
</div>

### Routing Between Pages

Coming from React.js, when you have to build a web application that has multiple pages, e.g. an e-commerce website, we make use of [React Router](https://reactrouter.com/en/main) or other routers for React.

All the routes would be listed in the entry point of the React app in order to emulate a Multi-Page Application (MPA) behaviour while React uses a Single Page Application (SPA) architecture.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you're confused by MPA and SPA, read this article <a target="_blank" rel="noopener noreferrer nofollow" href="https://blog.openreplay.com/single-page-apps-vs-multiple-page-apps/" style="pointer-events: none">SPA vs MPA</a> to gain some insight.</div>
</div>

In Next.js, routing between pages is really easy, and you don't have to define the structure of the router, you just follow the guidelines Next.js provides about folder structures. So essentially Next.js uses a file-system router.

However, at the point of writing this article, Next.js has two means of handling routing, the first means being the [**Pages Router**](https://nextjs.org/docs/pages/building-your-application/routing) and the second the [**App Router**](https://nextjs.org/docs/app/building-your-application/routing).

Both the Pages Router and the App Router work excellently though very differently and the in-depth differences between the routers are beyond the scope of this article 😅

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you're just getting started learning Next.js, I strongly recommend learning about the <strong>Pages Router</strong> first before the app router, cause lots of applications, and tutorials use the Pages router.</div>
</div>

Here's an example of how routes would be defined in a React app, using React Router v6.15.0

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693443139676/4dd32680-9b7b-40ff-bda3-56148bfe5a9c.png align="center")](https://reactrouter.com/en/main/start/concepts#defining-routes)

For Next.js, here's how the routes are defined in both the App and Pages Router using the file-system.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693510220233/1dd501df-a6c6-4477-8669-71e36cd487eb.png align="center")

Though it might look like lots of folders, but trust me, it's so much better 🤩.

### Optimizations

Hmm, optimizations, should I care about optimizations if I'm a newbie to Next.js and React?

Well, yes and no 😅

No, because you're still learning, and Yes because at some point you'd have to care about optimizations to make your app faster.

Optimations in Next.js come in various forms, but the essence of optimation is to improve the application speed and [Core Web Vitals](https://web.dev/vitals/).

> Since this article to geared towards newbies with Next.js, we'll not be going into all the optimization patterns Next.js provides but just two, that is Metadata and Image optimization.

#### **Metadata - Search Engine Optimization (SEO)**

Metadata is used to add helpful content about a web application, helping Search Engines like Google crawl and index the web application. Metadata isn't just for Search engines, social media also reflects metadata information of the site.

> For example, the image below shows the metadata information for [https://aichatbot.so/](https://aichatbot.so/)
> 
> [![AIchatbot.so](https://cdn.hashnode.com/res/hashnode/image/upload/v1693448079238/baf7e710-35c0-4e73-a321-b1368fc95a6e.png align="center")](https://aichatbot.so/)

Coming from React, managing metadata information isn't good at all, Well, there is this library [**react-helmet-async**](https://www.npmjs.com/package/react-helmet-async) which helps in some ways but it's no way compared to Next.js benefits.

If you'd like to know why React is bad for SEO, please go through these guides:

* [SEO For React Developers](https://youtu.be/j8OUmE4Vj3M?si=8KSJmJ784NUPPi1E) by [Codedamn](https://www.youtube.com/@codedamn) **(recommended guide)**
    
* [Is React Good for SEO? The Complete Guide in 2023](https://www.techmagic.co/blog/react-seo/#:~:text=React%2C%20out%20of%20the%20box,for%20both%20users%20and%20SEO.)
    

In Next.js, Metadata can be handled in two ways due to the Routers, i.e., the Pages and App Router.

Below is an example of how metadata is defined in Next.js:

![aichatbot.so metadata](https://cdn.hashnode.com/res/hashnode/image/upload/v1693451013389/ad474693-f7ca-4534-91a5-edafc0aa4bff.png align="center")

To learn more about Metadata in Next.js please visit the documentation:

* [App Router docs - Metadata](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)
    
* [Pages Router docs - Metadata](https://nextjs.org/docs/pages/api-reference/components/head)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you'd like to know more about metadata, read this guide - <a target="_blank" rel="noopener noreferrer nofollow" href="https://web.dev/learn/html/metadata/" style="pointer-events: none">Learn about Metadata</a></div>
</div>

#### **Image Optimization**

In Next.js, if you make use of the built-in image component, you get all the benefits of image optimizations.

Why do I need image optimization, you might ask?

Well, from the [Next.js documentation about images](https://nextjs.org/docs/app/building-your-application/optimizing/images) here are the benefits you get using the Image component.

* **Size Optimization:** Automatically serve correctly sized images for each device, using modern image formats like WebP and AVIF.
    
* **Visual Stability:** Prevent [layout shift](https://nextjs.org/learn/seo/web-performance/cls) automatically when images are loading.
    
* **Faster Page Loads:** Images are only loaded when they enter the viewport using native browser lazy loading, with optional blur-up placeholders.
    
* **Asset Flexibility:** On-demand image resizing, even for images stored on remote servers
    

> Hmm, what does visual stability mean, and the other benefits listed above 😕
> 
> To answer that question, I suggest watching this video which explains and shows you the benefits - [**Using Images in Next.js (next/image examples)**](https://youtu.be/IU_qq_c_lKA?si=9fDvfdoUPy_DvIY-) by @[Lee Robinson](@leerob)

### Data Fetching

Hmm, Data Fetching, but I can fetch data using the fetch API in React and also use a library like [Axios](https://www.npmjs.com/package/axios), and they all work fine.

Yes, using the fetch API and Axios works just fine, but with Next.js you get data-fetching features on steroids 🤩. Let's go over an example to get a feeling on how Data fetching in Next.js is really cool.

Let's say you're working on an E-commerce website with plain React, and on the product details page you have a single component responsible for the UI on that page cause it's basically going to be the same across all products.

Pictures speak better than words or text in this case, so below is an image showing two different products (shoes) with similar contents.

[![Jumia product page](https://cdn.hashnode.com/res/hashnode/image/upload/v1693491132163/391ab6d7-4093-47f6-a38c-2161de458e96.png align="center")](https://www.jumia.com.ng/)

Let's also assume the product details are coming from some API, and to get this to work in React, you'll have to fetch the data on the client (known as [**Client-side fetching**](https://nextjs.org/docs/pages/building-your-application/data-fetching/client-side)), whereby the user will get to the page first, and you probably show a loading state and then when the fetch resolves and the data is then displayed on the page.

The downside to this approach with React ([**Client-side fetching**](https://nextjs.org/docs/pages/building-your-application/data-fetching/client-side)), is that:

* The page wouldn't have the HTML structure for the product page, which is bad for SEO
    
* Also, when a particular product page is visited multiple times, there will always have to be a request to the API, getting the same data again and again.
    

Now, let's see how Next.js solves this problem.

> In Next.js there are a lot of Data Fetching patterns depending on the different use cases, but in this article, we wouldn't go over all the Data fetching patterns or techniques, we'll just go over the broad scope of how Next.js make data fetching better.

To solve the problem of the HTML structure not being in the shape of the E-commerce product page, Next.js does something called **pre-rendering.** From Next.js docs, Pre-rending is the process of generating HTML for each page in advance.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693496608990/9d6e1852-282e-49c8-af53-5d2152e745bd.png align="center")](https://nextjs.org/learn/basics/data-fetching/pre-rendering)

To solve the issue of always fetching the data when a page is visited, Next.js provides some data fetching patterns that can tackle this problem.

In the App router, we have [React Server Components](https://github.com/acdlite/rfcs/blob/first-class-promises/text/0000-first-class-support-for-promises.md) and [Server Action](https://nextjs.org/docs/app/building-your-application/data-fetching/forms-and-mutations) while with the Pages router, we have [getStaticProps](https://nextjs.org/docs/pages/building-your-application/data-fetching/get-static-props), [getServerSideProps](https://nextjs.org/docs/pages/building-your-application/data-fetching/get-server-side-props), [getStaticPaths](https://nextjs.org/docs/pages/building-your-application/data-fetching/get-static-paths) and more, which are grouped into two forms [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended) and [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering) 🤯🤯🤯🤯

> OMG, what's all this for data fetching 😭
> 
> Data Fetching is kind of scary in Next.js from all the Data fetching patterns it has.

Well, the good thing is that as a newbie in Next.js, you don't need to understand all just yet.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">A good guide that'll go over all this data-fetching craziness 😮‍💨 - <a target="_blank" rel="noopener noreferrer nofollow" href="https://nextjs.org/learn/basics/data-fetching" style="pointer-events: none">Pre-rendering and Data Fetching</a> by the Next.js team.</div>
</div>

The best Next.js data fetching pattern for the product details would be Static Generation, using the getStaticProps function on the Pages Router, which basically generates several HTML files for the product details page depending on the data from the backend API and then those HTML files are reused on the client, and cached in some Content Delivery Network (CDN), so there's no additional call to the server after build time.

[![Static Generation ](https://cdn.hashnode.com/res/hashnode/image/upload/v1693511253461/d7f5a9c0-f30b-4c87-9eaf-32768031bfb5.png align="center")](https://nextjs.org/learn/basics/data-fetching/two-forms)

As for the App router, the same thing happens, but we'll make use of server components which is the only option and they are amazing 🤩.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you don't understand all that was mentioned about Data Fetching, it's totally fine. I've left useful resources below, to guide you learn Next.js for free.</div>
</div>

## Conclusion

I'd like to believe I've been able to convince you and not confuse you 😏, that learning Next.js is the next thing you need to do in other to advance your React skills. Another motivation could be the Job market, most companies make use of some framework, be it Next.js, Remix and so many others out there. So learn a React framework, cause even the [React docs](https://react.dev/learn/start-a-new-react-project#nextjs-app-router) says so.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693513046940/34120b7c-bf3d-4c77-942f-707145d12a19.png align="center")](https://react.dev/learn/start-a-new-react-project#nextjs-app-router)

Finally, I'd like to say a big thank you to my friend @[Enis Jesugbogo](@Jesugbogo) for making me write this article speedily😅, by encouraging me to write before August 2023 is over, some hours left before the new month, so I hope Enis you're proud 😂.

Also, to all my readers, I promise to write from time to time now, Thanks for sticking around, much appreciation 💖

## Helpful Resources Learning Next.js

Disclaimer: Please learn about the Pages Router before the App Router if you're just getting started with Next.js. Then as you improve on yourself, look into the App router.

1. [Next.js Learning Documentation](https://nextjs.org/learn/foundations/about-nextjs) - The Next.js team were kind enough to put up this guide, that I followed to learn Next.js, though some things might have changed as to when I went through it, but it's a good place to start from. **Highly recommended. 🤩**
    
2. [**Next.js Tutorial for Beginners (2020)**](https://youtube.com/playlist?list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw&si=6yRUcBP8fmiRppeQ) - by the [Net Ninja](https://www.youtube.com/@NetNinja). This is a video guide which is quite old but it really teaches Next.js Pages Router principles really well. BTW, I just love learning new technologies from [Net Ninja](https://www.youtube.com/@NetNinja), cause I love his teachings 😍
    
3. [**Next 13 Crash Course 2023**](https://youtube.com/playlist?list=PL4cUxeGkcC9jZIVqmy_QhfQdi6mzQvJnT&si=Y-CCK9Cy4q9TRCy0) - by the [Net Ninja](https://www.youtube.com/@NetNinja). I haven't gone through it myself, but I'm sure it's great 💖
    
4. [**Next.js Documentation**](https://nextjs.org/docs) **\-** by the Next.js team. Though I don't recommend this documentation for learning, cause it doesn't work you through building an actual application. The documentation is useful when you want to know everything about some features with all the APIs and so on. 😊
    

With all of that, all the best learning Next.js, cheers 🍻 and see you in the next article 🎉

%%[buymeacoffee]