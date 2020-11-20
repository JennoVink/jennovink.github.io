---
layout: post
title: "My personal favourite ReSharper hotkeys."
date: 2020-08-26 10:50:07
categories: development
description: "I love using ReSharper! Here's how to step up your development game with the best hotkeys."
image: '/img/resharper_logo.png'
published: true
Tags: .NET VisualStudio ReSharper
---

Since my study (starting 2014) I used to work with a visual studio plugin called [ReSharper](https://www.jetbrains.com/resharper/). For me, Resharper is an excellent tool to **level up my productivity**. It provides an intuitive interface for refactoring code. In this post I would like to **share my favourite shortcuts & resharper functionalities**. This list is not in any order of preference.

### [Changing names](https://www.jetbrains.com/help/resharper/Refactorings__Rename.html){:target="_blank"} ```[ctrl + r, r]```
Often during the development process I know the structure (for-loops, altering data, etc) that globally needs to be programmed. After programming it happens that some variable names aren't descriptive enough in my opinion, which is a very natural thing to happing in that process. Although visual studio has a similar build-in functionality, it doesn't provide the following:

### In-place refactoring ```[alt + enter, enter]``` 
Although everyone has his own programming style, there is a need of standardised coding convention to make code more readable (by yourself and others). Thus, when naming a public property ```name```, this is corrected to ```Name```. By this way, when reading ```Name```, there is no doubt about its access modifiers.

### Move to \<class_name>.cs ```[alt + enter, enter]```
No one likes reinventing the wheel. In fact, a lot of problem I deal with during programming is already programmed by someone else. That's why I like standard solutions or examples I find on the Internet. But, sometimes the example I find online might not work. Embedding their solution into my own doesn't always works out OK. Copy-pasting a class under an existing class saves time (and clicks) in comparison to creating a new file and pasting the class into it, as the example class might not work in the solution.

### Search everywhere ```[ctrl + t]```
Searching in text? Looking for classes? Methods? Strings? Especially the \'magnifying glass\' icon is really handy as this moves all the search results in a separate view, making it more convenient to peek into the results by project.

### Insert constructor ```[Alt + insert]```
Writing a constructor one of the first things I learned during my study. Manually creating one, initializing a few of its class\' properties can be a lot of keystrokes (even with resharper\'s extensive code completion). Via this hokey, its really easy to select which properties/fields needs to be initialized right from the constructor. Although visual studio shares the same functionality, resharper has the choice to make parameters optional. A feature that visual studio doesn\'t have (yet).

