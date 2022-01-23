---
title: "Making github pages with hugo"
subtitle: "Also why bother?"
date: 2022-01-19T00:15:39+01:00
draft: false
---

I saw the github pages of [Conor Lamb](https://conorcorp.github.io) and he had a nice guide there highlighting the "easy" steps in setting up a "modern", "not outdated" type of "blog". Jokes aside, there's a reason why I decided to do it as well. Thanks Conor Lamb for the guide. It kinda helped! 👍

---

### What's Hugo?

Hugo is a static website generator that takes a theme, a list of markdown files, and some config and static content and makes it kiss and make a baby which is this site you're reading now.

### What's github pages

Ever seen one of those *"something.github.io"* websites? Well, apparently, if you:
1. Create a repository in your github account titled `<your account id>.github.io`
2. Go to repository settings and configure github pages for this repository
3. Slap some files in it
4. BAM!

There is a build pipeline happening, and the contents of your repository get displayed as a website.

### Picking a theme

This small step was actually harder than it sounds. A theme is what people see first, so it has to be:
* Easy to read. There are plenty of aggressive themes with hard to read fonts or too high contrast.
* Tuned for my use case. If I'm gonna write anything, it's going to involve code, diagrams, maybe charts.
* Uncluttered. The last thing I need is extra large bars at the top of code blocks that seem like code.
* Pretty. While the appeal of themes like Anubis according to the rest of the criteria is hard to resist, it doesn't allow me to appear human to you. For that, I needed you to see my friendly picture, so that you know that behind the image of a nerd there's a smiling person.
* It ... has to work. My first attempt was a disaster. Pretty theme, but didn't work with github pages, after a lot of headaches. Sad, but it's more about the content, right? And I have none yet. The theme is less important.
* License. Almost forgot about that one. I want my content to be of a permissive license. Some of the themes I looked at were GPL family, and I'm no laywer, but I don't want to get involved with having to have license issues as I use MIT, BSD, CC or [WTFPL](http://www.wtfpl.net/about/).

I could've also made my own. Although I am already in my pyjamas.
