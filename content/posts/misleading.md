---
title: "Misleading"
subtitle: "What is said isn't what's actually true"
date: 2022-08-09T01:42:43+01:00
draft: true
slug: misleading
summary: ""
categories:
    - Psychology
tags:
    - behavior
    - teams
description: |
    You, me, and everyone else, is lying, to themselves and to the others. Why is it bad and how can it be mitigated?
---

## you, and YOU

*What are your hobbies?*

What did you answer? If you answered truthfully, then you're among a minority of people who either came in prepared, with their System 2 activated, or you answer every day based on empirical evidence. Or maybe you really don't have any hobbies and you're OK with it, in which case other questions might trigger the same effect.

How do you know if you answered truthfully? Find a way to catalog what you do every day. Use empirical evidence for your answer. Many people that I know (and myself is definitely included) like to say a long list of unique hobbies. But when doing the actual remembering, 0% of my time in the last month were devoted to any of the hobbies that I usually list. Instead, my free time is spent doing chores, watching YouTube on a couch, going out for walks and shopping. But you don't say that to people who ask you about your hobbies.

So, the question is clear: *"What are your hobbies?"*. And what did you answer? Skiing, Hacking, Mountain Climbing, Violin? Did you really answer the original question, or did you switch it with *"What is interesting to me"*? Or maybe *"How I want people to see me"*? Or *"What I wish I could do"*? Think about what question would be more fitting to the answer that you actually provided.

So who are you *really*? You are the "you" that only the people closest to you, and Facebook, knows. Not even you know *you*. To yourself, you build an image, **YOU**, that is similar to *you*, but is from a near future, where things are slightly different from what they are today. If you're optimistic, then **YOU** is stronger, healthier, smarter, better organised, doing fun stuff and living the life. If you're depressed however, it's a worse situation than *you* are in.

**YOU** is the image that is displayed to strangers, it's the mask, it's our defense. **YOU**'s poop doesn't even smell. You know **YOU** very well, since you created this image. But few of us really know who we really are.

## Difficult answers

[Attribute substitution](https://en.wikipedia.org/wiki/Attribute_substitution) is the process in which the original question about us, is replaced in our mids with the picture of the image that we created. It's easier to answer questions about it, and the answers rarely suck that much in the case of optimists. We don't even think about it, and just proceed to answer this question. [Philip E. Tetlock](https://en.wikipedia.org/wiki/Philip_E._Tetlock) calls this "Bait & Switch", similar to the dishonest sales tactic sometimes used.

What about other aspects in life? In Tetlock's and Gardner's book, [Superforecasting](https://www.goodreads.com/book/show/23995360-superforecasting), this is mentioned in the context of people avoiding answers that are difficult to voice. One of those answers is "I don't know". When you're asked a question, you have to provide an answer, right? "I don't know" doesn't count as an answer, and makes you think that you just need to dig deeper. But that doesn't change the fact that you don't know, at least not immediately. In our lazy minds, dominated by [System 1](https://en.wikipedia.org/wiki/Thinking,_Fast_and_Slow), any answer that pops up that matches the heuristic conditions of the question being asked, is chosen as the answer. And we're sure about that.

Take any classical debate, like between a creationist and a follower of science, where the creationist would ultimately ask a question like "how did life first appear if it needs life for evolution to happen?", or "how did the universe appear?", and a follower of science would probably reply with something that is not actual facts. Actual scientists like to repeat, that it's OK to say "I don't know". There's lots of things we don't know. But in a debate with emotional stakes, this is the last thing on one's mind, and any answers that follows the heuristic "is it plausible" is being substituted for "known fact". Of course where the creationist is concerned, the standards for what passes as "fact" are significantly lower.

## Team communication

I work in software, and one might think that software engineering is no place for social sciences, the work of behavioral psychologists or debates between defenders of different philosophical ideas. But that can't be further from the truth.

Every day we communicate to people, who are either our team mates, our clients or contractors, and these subtle lies are everywhere, and they are costing millions, or even trillions of your favorite currency, on the global scale.

### Project estimation

How much will it take to solve this? The developer will often under-estimate, because the question is substituted, naturally, with a much simpler question to answer, which will have a simpler answer, and a shorter estimate.

I've talked to some teams that don't really qualify as "the most skilled developers", but they did one thing extremely well: they always finished all tasks from a sprint. To many, this would seem like a lie. I know, right? So how do they do it?

To estimate properly, you have to eliminate every single unknown. This means that any implementation description has to go into every single detail, about which credentials to use, which connection driver, how much logging there should be, what network resilience to factor in, etc. During the specification phase of such tickets, a lot of time is spent. Basically the majority of the blockers are removed or exported into separate tickets. It may take a full day for a sprint to be planned, but it's not time wasted on nothing. You make the further development faster, and most importantly - a lot more predictable.

### Debugging

Bugs are often very hard to solve. Some of them are even hard to diagnose. Couple that with the negative emotion associated with guilt for introducing this bug, and people will avoid finding it.

The following is almost always happening:

* The database technology is bad
* The framework doesn't work as it should
* This is a feature, not a bug

The worst is happening when several bugs are reported, and if one of them is more obscure and in a central place, developers will say that it's one bug that causes the rest, even if in fact they don't **KNOW** that. They may want it to be true, so they substitute the *"Is that the bug"* question with *"Would I want that to be the bug"*.

This miscommunication is costing a lot of time and money. Developers are misled by other developers, just because they didn't do the research, because that would require **System 2** to activate, when **System 1** already decided what the cause for that bug is. As a result, some developers will spend many days looking for a problem that doesn't exist, instead of spending 10 minutes looking where the initial claim came from.

## Mitigation

It's really hard to mitigate this even in yourself, so if you manage to mitigate it in other people, please contact me and tell me how you did that.

Be aware of this and other biases in yourself. Be careful with positive statements, and only make them if you can answer any questions with actual evidence for it. Otherwise be clear and use words like "I assume", or "possible". Make sure to be explicit about the level of your confidence in the manner, and a high level of confidence demands high quality evidence.

Be careful in your language and the thoughts you want to express, and make sure that they're factual.
