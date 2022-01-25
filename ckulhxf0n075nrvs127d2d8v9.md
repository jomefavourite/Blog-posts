## Introducing PlanDone - Getting plans done

Hello everyone 👋, this article is all about a fun project I decided to take to the next level by making it a Full Stack Application (which is my first) from just a school assignment project.

## What's PlanDone
PlanDone is a platform made for Students who would like to learn smart, be productive and access everything they need while studying in one place.

By giving students the ability to save their notes, tasks and forecast their Cumulative Grade Point Average (CGPA) score, which can all be accessed at any time. So now you can make sure you Plan and then complete (Done) 😏.

***[Github Repo](https://github.com/jomefavourite/PlanDone) / [Live Demo](https://plandone-student.herokuapp.com/)***

## Inspiration for the PlanDone
The year 2020 at December, Hashnode hosted a Christmas Hackathon, where an amazing project was built by @[Rutik Wankhade](@rutikwankhade) - *[How I built my own productivity app](https://blog.rutikwankhade.dev/how-i-built-my-own-productivity-app)* which is a Productive app extension for browsers I used for quite a while.

It's a great extension to quickly take notes, fill in tasks and so on. I really loved the idea behind the project so that's how I came about building **PlanDone**.

## Back story TL;DR
So at school, I took a Web Design class which is compulsory for all CS majors and at the end of that semester, we were tasked to come up with an idea for a project, using HTML, CSS, and JS which we were taught in class. 

After submitting about 3 project ideas to my lecturer, all were rejected for reasons I would never know :), then I thought of building an application that ties towards productivity because I could be really unproductive. Meanwhile, I was using @[Rutik Wankhade](@rutikwankhade) project as my browsers extension at that time and that's how I got the idea. I submitted the project idea to my lecturer and it got accepted 🎊.

Then, I built the frontend aspect *(more context below)*, making use of the browser's local storage feature to store users notes, tasks and links so that I could submit the assignment.

At this time, I was exploring backend technologies, so I said to myself, why don't I put my learnings into a project. So that's how the challenge started, making my first Full Stack Application.

## Features of PlanDone

**1. Creating Notes**

![Screenshot from 2021-09-29 01-38-55.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632876038604/lLMC_6OkM.png)

The notes created comes in different colours with the help of [Syntactically Awesome Style Sheets](https://favouritejome.hashnode.dev/write-css-with-superpowers-using-sass) features and a [Masonry Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Masonry_Layout) which I think is pretty cool.

All notes created can be edited and deleted, also notes are written in markdown format if signed up to the platform, *that's a special feature 😃*

**2. Creating Tasks**


![Screenshot from 2021-10-10 01-48-49.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633826994189/yTfmlaBNG.png)

Tasks could be anything you'll like to do, just add it with a deadline date. Once done, you click on the checkbox to mark it has done.

**3. CGPA Forecaster**

![Screenshot from 2021-10-10 01-56-12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633827597523/OMZnYhYiR.png)

![Screenshot from 2021-10-10 01-56-26.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633827650336/U5exjkDLU.png)

With this feature, students can easily see the score they need to work towards from their previous grades.

> This was a project done for Hashnode Christmas Hackathon 2020, view the article for the project here: [CGPA Result Forecaster - Hackathon Project](https://favouritejome.hashnode.dev/cgpa-result-forecaster-hackathon-project)

**4. Creating Links**

![Screenshot from 2021-10-10 02-05-17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633828324272/g0y2Q2Tzi.png)

The idea here is to add links to projects/articles/anything really, you might easily forget, this way you never lose a link you wanted to check out.

> **Quick Note** <br>
All the features above work both when a user signs in to the application and when they aren't signed in, the only caveat will be without signing in all information will be lost.

> **Also don't forget to give the project a star ⭐, if you think it's a fun project like I do 😎 - [https://github.com/jomefavourite/PlanDone](https://github.com/jomefavourite/PlanDone)**

## Built With
- **[Node.js](https://nodejs.org/en/)** for authentication, routing.
- **[Express](https://expressjs.com/)** for ease while working with Node.js
- **[EJS](https://ejs.co/)**: A template engine language that generates HTML markup with plain JavaScript. 
- **[SASS](https://sass-lang.com/)**: Sass is a preprocessor scripting language that is interpreted or compiled into Cascading Style Sheets.
- **[MongoDD/Mongoose](https://www.mongodb.com/)** for managing, storing or retrieving information.
- **[Heroku](http://heroku.com/)** for hosting the application.

## Planning, Building and Deploying

Here's where all the fun started, my first commit was on **Jun 21, 2021,** which was the time I had started making the project a Full Stack Application.

There was a lot of back and forth movement while planning and building the project, lots of tools were added and removed. I tried different tools, exploring as I build, which I'll say is good but it would have been better if I had my plans all laid out. 

*Leave a comment below, which you feel is better - Exploring different tools while you build or Having predefined tools to be used.*

- ### Planning:<br>
Since I already had an idea of what I wanted to build from @[Rutik Wankhade](@rutikwankhade) Project: *[How I built my own productivity app](https://blog.rutikwankhade.dev/how-i-built-my-own-productivity-app)*, it was easy to pick some fundamental tools I did use like EJS, Node.js, Express, SASS etc.<br>
<br>
Also, I created designs for the project with the help of [Figma](https://figma.com), first I did the wireframe for each page of the project.
<br>
<blockquote>
The wireframe was a requirement for school. If you'll like to know more about wireframe, [click here - How to wireframe a website](https://www.youtube.com/watch?v=2hQA1ZsGAH8)
</blockquote>
After completion of the wireframe, I moved then to the mockup of the website, which is a high-fidelity simulation of how I want the website to look.<br>
<br>
View the [Wireframe](https://www.figma.com/file/eyezgXHOUpwcu9n0tpT8F4/Student-Productive-Website?node-id=0%3A1)/[Mockup](https://www.figma.com/file/eyezgXHOUpwcu9n0tpT8F4/Student-Productive-Website?node-id=55%3A72) Designs

- ### Building:<br>
My building process started by setting up a Node application and figuring out how to set up Google authentication for the application, getting users Google data and tying their data into a database, so a user sees his/her information saved to PlanDone.
<blockquote>
**Quick Note:** Before figuring out the authentication processes, I had already done the Frontend aspect of the project where I made use of HTML, CSS, JS and also the browser Local Storage for store users information.
</blockquote>
With the help of some videos on YouTube, I was able to configure Google's authentication using *passport-google-oauth2* which is Google's strategy for signing up into web applications, more on that on their [documentation](http://www.passportjs.org/docs/google/). <br>
<br>
After I had figured out the authentication process, I moved into setting up my database, where I made use of MongoDB which is a NoSQL database making use of JSON-like documents with optional schemas. More on MongoDB here -*[Building A CRUD Application Using Node JS And MongoDB Atlas](https://blog.teachmebro.com/building-a-crud-application-using-node-js-and-mongodb-atlas)* by @[Altaf Shaikh](@altafshaikh).<br>
<br>
Thereafter I moved to implement other features I thought were cool, broke a lot of things, figured them out and generally learnt new things in the process. By the way, I made use of [EJS](https://ejs.co) which is a template engine language that generates HTML markup with plain JavaScript but in this case, I made use Node.js.<br>
<br>
Lastly, I had a lot of fun playing with SASS special features, creating custom Mixins, functions and the likes. If you'll like to read more about SASS, I've got an article here - [Write CSS with Superpowers Using Sass](https://favouritejome.hashnode.dev/write-css-with-superpowers-using-sass).

- ### Deploying<br>
<blockquote>
This was the most stressful part, at some point, I gave up for a while and continued trying once again.
</blockquote>
So the project is deployed to both Vercel and Heroku. It seems Vercel doesn't support **EJS**, so I couldn't get it running with Vercel, then I moved to Heroku. Heroku gave me a tough time, I just couldn't figure out why I wasn't able to view the project live. Even now I don't know what I did to make it work 😅, but it works finally after a series of errors.

## Resources used to Learn

- %[https://www.youtube.com/playlist?list=PL4cUxeGkcC9jsz4LDYc6kv3ymONOKxwBU]
- [NodeJS & Express - Google OAuth2 using PassportJS](https://www.youtube.com/watch?v=Q0a0594tOrc)
- [Node.js App From Scratch | Express, MongoDB & Google OAuth](https://www.youtube.com/watch?v=SBvmnHTQIPY&t=352s)

## Conclusion

It was a fun experience working with both Frontend Technologies and Backend Technologies, I look forward to building more Full Stack applications. So that's it, I wanted to share my experience building the application, hope it was a good read.

Also, If you'll like to contribute to the project, please do. I know there are a lot of bugs yet to be fixed, I might improve the project later on by making use of React or Next.js. 

> **Lastly, don't forget to give the project a star ⭐, if you like the idea behind the project 😎 - [https://github.com/jomefavourite/PlanDone](https://github.com/jomefavourite/PlanDone)**

**Thanks for Reading, do have a great day 👋** 









