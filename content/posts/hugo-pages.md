---
title: "Making github pages with hugo"
subtitle: "Also why bother?"
date: 2022-01-19T00:15:39+01:00
draft: false
tags:
    - hugo
    - this
categories:
    - Development
---

I saw the github pages of [Conor Lamb](https://conorcorp.github.io) and he had a nice guide there highlighting the "easy" steps in setting up a "modern", "not outdated" type of "blog". Jokes aside, there's a reason why I decided to do it as well. Thanks Conor Lamb for the guide. It kinda helped! 👍

<!--more-->

### What's Hugo?

[Hugo](https://gohugo.io/) is a static website generator that takes a theme, a list of markdown files, and some config and static content and makes it kiss and make a baby which is this site you're reading now.

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
* Pretty.
* It ... has to work. My first attempt was a disaster.
* License. Almost forgot about that one. I want my content to be of a permissive license. Some of the themes I looked at were GPL family, and I'm no laywer, but I don't want to get involved with having to have license issues as I use MIT, BSD, CC or [WTFPL](http://www.wtfpl.net/about/).

I could've also made my own. Although I am already in my pyjamas.

### Automated deployments

If you do theme switching until you figure out what you want, you will have the trouble that I had:

**your content is in the same place as the config**

Managing versions, revering them would be a pain. So I did 2 separate repos. One purely for [content](https://github.com/apisarenco/apisarenco.github.io), and another one purely for [configuration](https://github.com/apisarenco/hugo-github-pages).

It builds a branch called `build` in the "content" repository, where all the static files are hosted, as soon as I update any content, or manually run the build.

I'm still getting the hang of it, so here's how it works so far:

You can add a definition in `.github/workflows` directory in your repository, and it will run when certain conditions are met. [Here's mine](https://github.com/apisarenco/apisarenco.github.io/blob/main/.github/workflows/deploy-gh-pages.yml), for this automatic build. It basically does the following:

1. Clones the `configuration` repo
2. Clones the `content` repo
3. Clones the `build` branch of the `content` repo separately
4. Downloads the latest release of hugo, as a binary, copies content next to config, and runs the `hugo` command, and then copies the artifacts to the `build` directory
5. Creates a commit with the changes and pushes it to `build` branch if there are any changes detected

The reason for a separate `content` and `build` directories from the same repository is that `content` is read-only, and I always get the freshest copy, while `build` is write-only, and will see incremental updates, trackable in git, to the conte that it manages, without any merge conflicts.
