---
title: "that one time i pushed multiple bugs into production"
seoTitle: "that one time i pushed multiple bugs into production"
seoDescription: "I pushed multiple bugs into production of a live site, here's how I fixed them"
datePublished: Fri Mar 10 2023 00:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clf1ruxy606hihxnv370k7cfs
slug: that-one-time-i-pushed-multiple-bugs-into-production
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678896800920/b96aecd2-c650-4ff0-888f-87f27eaa873a.jpeg
tags: web-development, wemakedevs, debuggingfeb

---

### a little context

So, earlier this year, I was messing around with my [web portfolio](https://cybergenie.netlify.app). I wasn't doing anything significant, just moving a few projects around and switching Tailwind to the CLI from [Play CDN](https://tailwindcss.com/docs/installation/play-cdn) in Vue. I hoped to shoot some shots with this portfolio, so I figured I'd update my details and take care of some security issues that GitHub had been nagging me about. Little did I know that my worst all-night-long debugging experience had just begun.

![mail i got from github](https://cdn.hashnode.com/res/hashnode/image/upload/v1678396448308/1876103b-c685-4b2f-8282-ebf7ec713f0a.png align="center")

I got several emails that the repository my portfolio was sourcing was facing 'high severity' security vulnerabilities, but I didn't understand what it meant. After I got the 15th email (yes, I actually counted) with a different vulnerability each time, I figured it was time to check out what the issue was.

### the bug

My dependencies were outdated and the various versions weren't compatible with each other. That was it. The site was live. Working fine without hitches. The only thing that bothered me was the continuous emails.

> You know that saying, "if it ain't broke, don't fix it?" Yeah, I totally ignored that and I regretted doing that. Lesson learned, folks.

### when I thought I found a fix

Having no previous knowledge of what I was about to do, I headed over to the repositories' security tab, where I could find details of the issue. I found out that you can actually set up something called 'dependabot alerts' that will notify you once a dependency is outdated and is causing security breaches or other related problems, and automatically raise a pull request with the latest version of that dependency.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678398698009/abc5af7d-c69c-4097-91df-fb44260dd15d.png align="center")

I had 23 of these alerts with corresponding pull requests, and I thought merging these pull requests would fix the issues. So I went to work. Merged every single pull request that was opened and updated all the dependencies for the project. Since the pull requests were opened at once, I had to rebase the changes after merging every PR. It was a cycle of merge - `git pull` - `git commit` - `git merge`. The PR list was finally empty and life seemed good at that moment. Just when I thought I had fixed the bug...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678399398244/e4d4cd9c-08bb-4ec6-b14a-ddb73f10d829.png align="center")

Yeah, you see those red-colored labels tagged 'failed'? That was me breaking production with every PR I merged. It was chaos. At this point, the site was already down. What made it worse was that I had just applied for an opportunity. What were the odds that they didn't tap the link immediately? I tried not to let my thoughts overwhelm me as I tried to figure out what this new development was.

The unexpected debugging began. At this point, I didn't know what to do, or where to start. I tried to frame my issue into different questions with different keywords for my Google search, but I wasn't getting any helpful results. Searched various articles and references I came across, but nothing. Even the renowned StackOverflow didn't have an answer. That was when I knew things were terrible.

The first fix I tried was to revert all the PRs I had merged. This resulted in multiple merge conflicts which, in the end, didn't work. One thing I knew was that the bug had something to do with conflicting versions of dependencies, so the next thing I tried was reverting it back to how it was before any of the merging was done. I searched my commits for the last successful deployment and fetched the `package.json` file where the dependencies are usually saved. I compared the current content of the file with this last successful version and found the lines of code that were different, copied the content of the old file, and pasted it into the current one. Then I pushed the changes and hoped for a change in the error message. As expected, I didn't work. But I got a hint of what exactly the issue was and how to solve it.

### the actual fix

When I was comparing the two files, I noticed 2 dependencies (`webpack`and `webpack-dev-server`) that had a major change. So I made some research and found out that the versions which both were updated to wasn't stable, and thus weren't compatible. I searched for the last stable version of both that would work together and noted them down. The next thing I did was delete the entire `node_modules` folder, the `package.json` file and the `package-lock.json` file. I wanted to start the dependency installation from scratch so that I wouldn't miss anything. I ran `npm install` to bring back the `node_modules` folder, and then inserted the exact combination of dependency versions that were compatible into the `package.json` file. Then I pushed my changes with both eyes closed, hoping that the 'magic' trick I just performed would work. And yes, it did. The site deployed successfully, and production went back live. Phew.

### lessons and conclusion

Getting bugs can be very frustrating, but it's part of the everyday life of a developer, so I've learned to live with it. No, I didn't hear back from the recruiter, but I learned so many things while dealing with this bug, including the fact that StackOverflow doesn't have all the answers. It's important to pay very close attention to details because the error might be in front of you the whole time. Most importantly, *if it ain't broke, don't fix it*.