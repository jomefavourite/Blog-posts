---
title: "Overcoming Challenges When Moving from Create React App (CRA) to Vite: Debugging Tips"
seoTitle: "Overcoming Challenges When Moving from Create React App (CRA) to Vite"
seoDescription: "In this article, I'll go over the 5 challenges I encountered in migrating and updating dependencies, how I fixed them, and some Vite-specific things."
datePublished: Wed Mar 08 2023 18:20:50 GMT+0000 (Coordinated Universal Time)
cuid: clf00a24q000108l2dsgzb5ss
slug: overcoming-challenges-when-moving-from-create-react-app-cra-to-vite-debugging-tips
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678296189061/1f472db1-8ab6-4587-9ffd-8d7e0262ea9b.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678295946334/dce63616-6577-4531-9986-870406777dea.jpeg
tags: debuggingfeb, debuggingfeb-writeathon

---

At my work, we have a reasonably large codebase using Create React App (CRA) and the codebase started feeling slow, starting up the server took forever, and hot module reload took forever to reflect changes on the browser also, so at that point, I knew I had to move to the **Next Generation Frontend Tooling - Vite 🔥**

In this article, I'll go over the 5 challenges I encountered while migrating from CRA to Vite and updating dependencies, how I found solutions to the challenges and some Vite-specific things that just had to be done.

Please note that this article is centered on the libraries which my work codebase uses, so it might not cover all possible errors, you might encounter will migrating from CRA to Vite. Some of the libraries mentioned in the article and used in the codebase are:

* [MUI](https://mui.com/)
    
* [React](https://reactjs.org/)
    
* [React-phone-input-2](https://www.npmjs.com/package/react-phone-input-2)
    
* e.t.c
    

---

## Context before Successfully Migrating to Vite

Before I successfully migrated from CRA to Vite, I had failed in the past and given up because of the pill of errors I encountered. The way started the process of migrating was by finding articles about the migration process and following them, step by step, yet I ended up with errors the articles didn't account for.

So I decided to go with the divide-and-conquer approach (without recursion 😏), by initializing a Vite project from scratch and setting up the project gradually, while adding new necessary files from the CRA codebase to the Vite codebase.

Essentially, I had two branches managed by git, one for the codebase with CRA and another with Vite. The Vite branch was pulled from the CRA branch but then all the files were deleted to initiali[z](https://github.com/vitejs/vite/issues/769)e the Vite application.

> There might have been a better way for this process, but that's what I did, and it's tedious but it works 🤧

---

## Challenges and Errors I encountered

### 1\. The JSX syntax extension is not currently enabled

The very first error I encountered was: **The JSX syntax extension is not currently enabled** which means that if you have a file that has a React component that returns JSX, then the file extension should be **.jsx** and not **.js.**

Here's how the error shows on the terminal:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677716627119/e5722fcc-7295-4880-ae11-b4561326f618.png align="center")

All the files in the codebase were using **.js** as the file extension and now Vite was saying I have to move 50+ files to **.jsx** 🤯.

Evan You, the creator of Vite, gave a good reason why **.jsx** extension should be used with files that return JSX. The response from Evan You was mentioned in the issue: [Add an option to transpile .js file with build · Issue #769](https://github.com/vitejs/vite/issues/769).

[![Evan You Response To: Add an option to transpile .js file with esbuild](https://cdn.hashnode.com/res/hashnode/image/upload/v1677717208376/e5fd9239-7f8f-4bbe-a6b4-65ac895ba8b2.png align="center")](https://github.com/vitejs/vite/issues/769#issuecomment-780593283)

### Solution

The way I overcame this challenge was by using a tool called [**PowerToys**](https://learn.microsoft.com/en-us/windows/powertoys/) created by Microsoft. It comes with a feature named **PowerRename,** which allowed me to rename multiple file extensions at the same time quickly. So I renamed all the file extensions from **.js** to **.jsx** provided the file contains some form of JSX being returned.

> Visit here to learn about the feature PowerRename offers: [PowerToys PowerRename utility for Windows | Microsoft Learn](https://learn.microsoft.com/en-us/windows/powertoys/powerrename)

### 2\. Upgrading dependencies in the codebase

Since I was already making a large change to the codebase, by migrating from CRA to Vite, I thought to myself, why not update all the dependencies to the latest and greatest version?

*Honestly, I don't know who sent me to do this, cause it ended up being a terrible experience 🤣*

One of the dependencies that had lots of breaking changes was Material UI now called MUI. Before upgrading, Material UI v4.11.2 was used in the codebase along with some of its peer dependencies like Material Icons around similar versions.

Upgrading to MUI v5 introduced a lot of changes, to where components were imported from, all the packages' import names were changed from `@material-ui/*` to `@mui/*,` and many more changes.

I mean, just look at this mess MUI put me through 😅

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678268478242/08657db3-3571-42af-8325-a6227ccda445.png align="center")](https://mui.com/material-ui/migration/migration-v4/#replace-all-imports)

Other dependencies had some changes too, which I had to implement due to the upgrade, but none was as stressful as MUI, hence, I'm only mentioning MUI in this section.

Another problem that came with upgrading Material UI was changes to where components are imported from. For example, the Button component in Material UI v4 is imported from `@material-ui/core/` while MUI v5 is from `@mui/material/`. So I had to be aware, that not only the prefix `@material-ui/` was changed but also

*Material UI v4 example for the Button component:*

```typescript
import Button from '@material-ui/core/Button';
// ----------------- OR -------------------- //
import { Button } from '@material-ui/core';
```

*MUI v5 example for the Button component:*

```typescript
import Button from '@mui/material/Button';
// ----------------- OR -------------------- //
import { Button } from '@mui/material';
```

So how did I overcome the changes that MUI brought?

> I failed to upgrade from React 17 to 18 in my work codebase because I wasn't ready for the stress, especially now that components are rendered twice and I might need to change the architecture of how useEffect is used 😏.
> 
> Maybe I'll do this later in the future... 😤

### Solution

There was no way I could go over 500+ files that depended on Material UI and change them to the new MUI structure manually. To overcome this challenge, I relied on VS Code Search and Replace feature.

From the image below, you'll see that 601 files had the word **@material-ui/**, which needed to be replaced with **@mui/**. Luckily for me VS Code did the replacement in a bliss.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678271655654/c33dc8fe-57ee-482c-a60c-9c0b1cb3a036.png align="center")

Using the Search and Replace feature in VS Code, I was able to quickly make global fixes on the codebase.

Reading the documentation for the dependencies I upgrade was a huge help, like documentation of MUI has a migration step, so I was aware of the breaking changes, which can be found here: [Migrating to v5: getting started - Material UI (](https://mui.com/material-ui/migration/migration-v4/#replace-all-imports)[mui.com](http://mui.com)[)](https://mui.com/material-ui/migration/migration-v4/#replace-all-imports).

### 3\. Error: Minified React error

The error ***Minified React error*** was caused by the library [`react-phone-input-2`](https://www.npmjs.com/package/react-phone-input-2) used in the codebase. This error was also one that gave me a tough time, to figure out, cause it worked fine on the development server but shows the error on production.

The root of the error, explained by data is that many packages follow a bad practice that breaks Rollup ESM-CJS interop.

> Truthfully, I don't know enough about how Vite works with Rollup, and how libraries are made, so I'll direct you to the root of this error, explained data here [https://github.com/vitejs/vite/issues/2139#issuecomment-1024852072](https://github.com/vitejs/vite/issues/2139#issuecomment-1024852072)

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678278432335/e09f0f19-d6ae-41ad-80ea-a692465b102c.png align="center")](https://github.com/vitejs/vite/issues/2139#issuecomment-1024852072)

Fortunately, the discussion about the problem on the Vite repository led me to discover a solution.

### Solution

Before I mention the solution, here's the issue raised for the error on the Vite repository: [Encountered “Minified React error” in the production environment](https://github.com/vitejs/vite/issues/2139)

It has 71 participants contributing to the discussion and still the issue isn't closed, so it seems there are still some libraries that may cause the error.

The solution to this problem was to check if the imported component has the property `default` if it has the property `default`, then the default component should be used otherwise the component should be used.

Here's a snippet to check for default components in the `react-phone-input-2` library and the solution to my problem.

```javascript
import RPI from "react-phone-input-2"; 

const ReactPhoneInput = RPI.default ? RPI.default : RPI;
```

Thanks to [Kylar13](https://github.com/Kylar13) for his comment, I was able to detect that it was the `react-phone-input-2` library that was giving me the error, but then from the issue discussions, I could have other libraries installed that could have the same problem.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678279616052/72ea048d-753d-423c-ac5a-afe9866b3dac.png align="center")](https://github.com/vitejs/vite/issues/2139#issuecomment-1133130323)

So I needed a permanent fix, luckily after going through the 80+ comments on the issue I found a permanent fix posted by [Boni0](https://github.com/Boni0).

Here's the full discussion by Boni0: [https://github.com/vitejs/vite/issues/2139#issuecomment-1399098579](https://github.com/vitejs/vite/issues/2139#issuecomment-1399098579)

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678280270865/84d04281-b70a-4f0e-8f94-b20e542bb57d.png align="center")](https://github.com/vitejs/vite/issues/2139#issuecomment-1399098579)

But here's the solution I ended up using in my codebase, which works fine now.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678280450807/0233c2b8-385f-4710-87be-726a5b4f66dd.png align="center")](https://github.com/vitejs/vite/issues/2139#issuecomment-1405624744)

### 4\. Uncaught ReferenceError: makeStyles\_default is not defined

This is one of that errors that can make one cry and regret migrating to Vite 😅. Why do I say this? (*assume you heard me ask the question 😄*) Because the error is unpredictable and comes and goes while blocking you from doing anything in development. Also, the error comes in different forms, it could be `Uncaught ReferenceError: Box_default is not defined`.

I guess the issue is with MUI, not working properly with ESM or something like that, though I found a solution that works, I can't say the root of the problem.

### Solution

Remember I mentioned the error is unpredictable, so take this solution with a grain of salt, cause I don't know why the issue comes up.

From the issue - [Exported variable in chunk is not defined · Issue #1853](https://github.com/vitejs/vite/issues/1853), I found out it's better to use [named import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#named_import) while importing components from MUI.

So use this:

```javascript
import { Box } from '@mui/material';
```

Instead of:

```javascript
import Box from '@mui/material/Box';
```

Also, from the issue, it was mentioned to add `esm` as the suffix to the package MUI.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678284575117/3bbf10ad-34b9-4aa5-90e5-b9fc118747f1.png align="center")](https://github.com/vitejs/vite/issues/1853#issuecomment-793026832)

So I did this on my end, in the `vite.config.js` file:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678285108690/25e73dff-9b5e-43b1-a3ae-e326780d00f2.png align="center")

### 5\. Uncaught TypeError: styled\_default is not a function

This error is also one that's unpredictable and is caused by MUI. I've encountered this error more than once, and I haven't found a permanent fix for it, I just hope I wouldn't see it again.

The error doesn't allow me to make changes on development, so all I saw on the browser is a blank white screen, hence I had to fix it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678285227445/52000ce9-d03b-40f5-960d-0a0014f062c4.png align="center")

At the point of writing this article, I still got this error and here's a comment I made on the issue - ﻿ [Popper.js:9 Uncaught TypeError: styled\_default is not a function](https://github.com/mui/material-ui/issues/32727)

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678285829860/1be4618f-b1e1-46cd-ba72-06dde7f41ab2.png align="center")](https://github.com/mui/material-ui/issues/32727#issuecomment-1447936047)

### Proposed Solution

From the issue mentioned above, the solution which works most time is to delete the `node_modules` folder and reinstall all your dependencies.

Another solution that worked for someone is to use `@vitejs/plugin-react-swc` instead of `@vitejs/plugin-react`.

I have tried all the proposed solutions on the issue - [Popper.js:9 Uncaught TypeError: styled\_default is not a function](https://github.com/mui/material-ui/issues/32727), must times it works, while sometimes it doesn't. I'll leave it at that, though currently, I don't get the error.

## Conclusion

Do I regret migrating from Create-React-App to Vite? No, maybe a little, Yes, cause I have to go through lots of issues to figure things out.

Was there an improvement in server startup time, installing dependencies, and production build? Yessss, Vite is so fast. Blazingly fast ❤️‍🔥.

---

So I cloned the legacy codebase, the one using Create-React-App, installed the dependencies and started the server. It took **5 min, and 34 sec** for the server to startup and reflect on the browser 😫.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678290350144/ad5534ba-866d-463a-bd09-824184ffc607.png align="center")

The above test was done when I was starting the server for the first time, the second time I started the server, it took **1 min and 33 secs** which is fairly okay I guess. But Vite took **35 secs** for the browser to show the webpage fully loaded though it wasn't the first time I had started the server.

---

Would I ever use MUI for any reason in the future? Definitely, NO. If not that it would be a tug of war to remove MUI from my work codebase, I would have removed it.

With all of this, I leave with this, if you're migrating from CRA to Vite, and you're using MUI in your codebase, just know you're in for soup 🤣.

If you found this article helpful in a way, do like, sh, are, and follow me for more articles. Also, if you have a simpler approach or solution to solve the issues I mentioned in the article, please drop them in the comment, I'll love to see them.

I'll make sure to keep this article updated if I encounter more errors or bugs due to the migration.

**Thanks for reading!**