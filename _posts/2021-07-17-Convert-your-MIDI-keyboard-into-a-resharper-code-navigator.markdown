---
layout: post
title: Convert your MIDI keyboard/pad into a resharper code navigator!
description: A project I did in my sparetime to navigate quicker through code.
date: 2021-07-17 12:30:00
hero_image: https://img.youtube.com/vi/nENmCYmhjuY/hqdefault.jpg
hero_height: is-large
hero_darken: true
image: https://img.youtube.com/vi/nENmCYmhjuY/hqdefault.jpg
tags: hobby dotNet MVVM Software
---

## The story behind this project

Checkout the [source code](https://github.com/JennoVink/MidiKeyboardResharperCodeNavigator).

In another blog post, I created a [midi keyboard soundboard](/2020/05/08/Convert-your-MIDI-keyboard-into-a-soundboard/). When I'm navigating through a larger codebase, I thought it's neat to have buttons to navigate to bookmarks. That's why I decided to upgrade the existing soundboard project. The following midi pad is used (see picture below):

![AKAI LPD8 picture](/img/akai.jpg "AKAI LPD8 used in this project")

Instead of playing sounds, I used [`System.Windows.Forms.SendWait()`](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.sendwait?view=netframework-4.7.2){:target="_blank"} to send keystrokes to the computer. These keystrokes maps to the resharper bookmarks. In this case, ctrl + <number> (go to bookmark <number>) or ctrl + shift + <number> (toggle bookmark <number>). 

Using the application, navigating through code is more intuitive. Instead of [going back- and forward](https://docs.microsoft.com/en-us/visualstudio/ide/navigating-code?view=vs-2019){:target="_blank"} all the time, use bookmarks. It's easy to toggle a bookmark: just double-tap a button. A single tap will navigate to the particular bookmark.

I used my application for a week now, and it's working for me: most of the times I know exactly where to navigate in a large codebase. Having bookmarks getting there is just a lot easier.

Fun fact: other applications also use ctrl + <number> to navigate. E.g. Google chrome uses ctrl + 1 to go to tab 1.