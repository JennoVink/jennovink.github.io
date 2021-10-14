---
layout: post
title: "Stepping up my dotnet game!"
description: "Finished a pluralsight course on design patterns and refactoring."
date: 2021-10-13 20:00:00
hero_image: /img/pluralsight-badge.svg
hero_height: is-medium
hero_darken: true
image: /img/pluralsight-badge.svg
published: true
tags: dotNet DesginPatterns Software
---

## Full course on design patterns

One thing what's especially important as a developer is to invest time and effort into learning new theory about software engineering. One of the topics I would like to write about is design patters which I recently finished a [pluralsight course](https://app.pluralsight.com/paths/skill/design-patterns-in-c){:target="_blank"} on. In 13 hours, 25 design patters are covered. Although not every design pattern is really useful for me (e.g. flyweight), I highly recommend taking this course as this is a good refresher if you already have some OOP skills. Besides this course, I red the book 'Head First Design Patterns' which I found really interesting (more practical examples). The thing with design patterns is:

> It's easy to write code a computer can understand, but hard to write code a human can read.

This is where design patterns comes in place. You don't have to reinvent the wheel to create solutions that are more maintainable and easily extendable with new business requirements.

### Rules engine pattern

For one of [Lijnco's](/2021/04/05/starting-a-new-chapter-at-Lijnco) customers I was building an order file validator. The file had to follow certain rules. I'll name some of them:

* All the products had to exist (relatively complicated check, not a simple database lookup. I won't go any further into details).
* The order amount had to be a multiple of 5.
* The file ([fixed-width](https://www.softinterface.com/Convert-XLS/Features/Fixed-Width-Text-File-Definition.htm){:target="_blank"}) can't contain any tabs (\t).

When one of these rules aren't met, the customer receives an email with a readable error message.

One of the things I really like, is to learn something and imediately use it in the real world. This is a good example of that.

Instead of writing a few if-else statements, I decided to use the 'rules engines design pattern' which made it really easy to add/remove new rules later on. Besides that the workings of the code could be validated more easily via unit tests. This is a good thing when you're doing [test-driven development](https://nl.wikipedia.org/wiki/Test-driven_development){:target="_blank"}, one thing I try to do when I'm working on new source code.

One thing to print out for yourself as a good reference is this [cheatsheet](http://www.celinio.net/techblog/wp-content/uploads/2009/09/designpatterns2.jpg){:target="blank"}, although its descriptions are little hard to digest.

---

Note that the hero image was created by [pluralsight](https://www.pluralsight.com/){:target="_blank"}.