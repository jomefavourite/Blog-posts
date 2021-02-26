## CGPA Result Forecaster

Hello 👋, here's my submission for Hashnode Hackathon Powered by Vercel. It's a __Grade Point Average (GPA)__ and __Cumulative Grade Point Average (CGPA)__ calculator with a special feature which is to forecast the average score a student needs to end up with a 1st Class, 2nd Class Upper/ Lower per semester from his/her known scores.

![ezgif.com-gif-maker (3).gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1611787552869/ER7aHwapC.gif)

## Inspiration for the project

During any exam period, I'll sit down, open up Excel sheet, inputs my current courses grades with their credit unit to formulating potential grades I could get to end up with a first-class (I like to aim high 😊) from my current grades. Then I thought of an idea, could I make a website that does this for me? 

The idea faded away because I said to myself, it's too complicated for me to achieve even without trying.

On December 22nd, Hashnode Christmas Hackathon was announced but I couldn't come up with an idea for the hackathon then a week later, I got a message from a friend [Rhoda](https://twitter.com/DOctDevv) asking for a suggestion on what to build for the hackathon. 

After thinking for awhile my old idea came to mind and I pitched the idea to her then we started working on the project but eventually stopped since the deadline for the Hashnode Christmas Hackathon passed. 

Thankfully, another hackathon was released and the motivation for the project was revived again, hooray! 🎉🎉

## Planning the project

Planning how the project should work and look was a lot of stress but I came up with a structure as a guide of how the end product should be, well at least something just to get started with.

> There have been a lot of changes added to the final design from the sketches below.
 
![pic1.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1611587036658/W_7KVqDAl.jpeg)

![pic2.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1611587048154/lOfLBZ-yQ.jpeg)

Also, I came up with a guide for what features should be implemented:

![pic3.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1611587521681/BXfdLHc9_.jpeg)

![pic4.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1611587524478/rnFazI0Ix.jpeg)

While working on the project at the earlier stage, I did a lot of implementation of the features by myself even without telling my comrade - [Rhoda](https://twitter.com/DOctDevv), so a better teamwork practice was needed and we worked on that.

## Grade System of the project

This project makes use of my Universities grade system and also most schools grade system which is :

| Score Range | Letter Grade | Grade Value |
|------------- |--------------|--------------|
| 70 - 100       | A     |  5      |
| 60 - 69          | B  | 4   |
| 50 - 59 | C | 3 |
| 45 - 49 | D | 2 |
| 40 - 49 | D | 1 |
| < 40 | F | 0 |

|Final - CGPA  (FCGPA)    |     CLASS OF DEGREE. |
|------------- |----------------|
|4.50 - 5.00 | 1st Class. |
|3.50 - 4.49    | 2nd Class Upper |
|2.50 - 3.49   | 2nd Class Lower |
|1.50 - 2.49   | 3rd Class |
|1.00 - 1.49   | Pass |
|0.00 - 0.99       | Fail |

If a user tries using the application on any other grade system apart from this, I'm afraid it won't work as expected.

## Challenges encountered

- __Implementing main feature__

After getting a basic ideal look and functionalities for the project the main feature (which is to get the average score a student needs to end up with a 1st Class, 2nd Class Upper/ Lower per semester from his/her known scores. ) was difficult to figure out and implement.

> To demonstrate the challenge, here is a scenario for the calculation.

For example, you're on a __4 years__ program at a University. That means you'll need 8 GPA scores in totally and you're only done with the first year so you have 2 GPA scores.

So, therefore, there're __6__ unknown GPA scores left. Let's say the first 2 GPA scores gotten are __3.65__ and __4.32__. Then you'll need __4.671666667__ as an average to end up with a __4.50__ (a first-class) at the end of the __4 years__ program.

<span id="example"></span>

```js
(3.65 + 4.32 + (4.671666667 * 6 )) / 8 = 4.5
```

From the calculation above, an algorithm needed to be created that when used on whatever current GPA's you have it'll still derive the average score.

This part was tricky, I couldn't figure it out on my own, so I asked one of my teachers who tutored me on Mathematics when I was to gain admission into the University. He came up with a Mathematical algorithm I can use to solve this problem. 

All I had to do was to implement the mathematical algorithm into code, in order for the application to work. This was tough, but after searching Google and [Stack Overflow](https://stackoverflow.com/) for answers having in mind the idea I wanted to bring to code, I finally found answers.

> Big thanks to Stack Overflow

- __Average score display__

Another little challenge we had was with the average derived score. It could be in decimal places just like from the [example above](#example) - __4.671666667__ (9 decimal places). This was a problem because the decimal places could be up to 12 and so on. I had to figure out a way to make the average score into a 2 decimal place fraction. 

Meanwhile, If I just picked only the first 2 decimal from the fraction (__4.671666667__) that will be __4.67__ it wouldn't add up to __4.5__ anymore.

```js
(3.65 + 4.32 + (4.67 * 6 )) / 8 = 4.49875
```

Then I decided to calculate for

- __4.52__ for a 1st Class instead of __4.50__
-  __3.52__ for a 2nd Class Upper instead of __3.50__
- __2.52__ for a 2nd Class Lower instead of __2.50__

Doing this allowed me to be able to round whatever decimal place the average score is to a 2 decimal place.


> For example, into __4.60__.

Also by increasing the scores to be calculated to __4.52__, __3.52__, __2.52__ the average score isn't exactly going to round up to the scores respectively because they'll be rounded up to 2 decimal place but they will be in the range of __4.50__ to __4.52__ and so on for other scores at least not below __4.50__ or __3.50__ or __2.50__.

## Bonus Feature

After the entire functionalities were completed, I thought what else is missing. Then I came to the conclusion it's making the app a __Progressive Web Application (PWA)__

At the moment of the thought, I had no idea how I'll implement a PWA functionality. So I asked [Rhoda](https://twitter.com/DOctDevv) if she knew how PWA works, thankfully she knew how it works. 

[Rhoda](https://twitter.com/DOctDevv) implemented the PWA functionality and I learnt from how she did it.

Also after some testing, we noticed the application might not be easy to utilize so Rhoda implemented a need help modal, which displays to the users how the app should be used.

![scrnli_2_2_2021_3-31-26 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1612276304444/tX4AcLKD0.png)

---

[Live Demo hosted by Vercel](https://cgpaforecaster.vercel.app/)

[CGPA Result Forcaster Repo](https://github.com/jomefavourite/CGPA-Result-Forecaster)

## Conclusion

I had a fun experience making the app work and also working with someone. All I hope for is that students would find the app useful as I would.

Thanks to [Rhoda](https://twitter.com/DOctDevv), Mr Victor (my maths instructor) and Stackoverflow for helping to make this project a success. Hopefully, I'll improve on the project later on, by making it a mobile application.

P.S This project also belongs to [Rhoda](https://twitter.com/DOctDevv) because she did put in a lot of effort making the project.

Thanks to Hashnode for making me fulfil this project 😊.










