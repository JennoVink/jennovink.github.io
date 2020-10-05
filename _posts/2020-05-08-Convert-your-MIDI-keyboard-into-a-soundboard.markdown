---
layout: post
title: Convert your MIDI keyboard/pad into a soundboard!
description: A project I did in my sparetime to practice MVVM and working with MIDI.
date: 2020-05-08 09:00:07
hero_image: https://img.youtube.com/vi/nENmCYmhjuY/hqdefault.jpg
hero_height: is-large
hero_darken: true
image: https://img.youtube.com/vi/nENmCYmhjuY/hqdefault.jpg
tags: bulma-clean-theme jekyll docs
canonical_url: https://www.csrhymes.com/2020/05/08/creating-a-docs-site-with-bulma-clean-theme.html
---

I created Bulma Clean Theme as a theme for my own website and decided to open source it so others could use it as well. One of the key things I wanted to do was to create a theme that worked with GitHub Pages, which also means that you can also use it as a docs site for your project. 

## The story behind this project

As a hobby I started exploring to create digital music which I listen every now and then. Besides that, I used to play piano when I was younger. Thus, I bought a simple midi pad (AKAI LPD 8, see picture below).

Each of these buttons and knobs can be configured in Ableton (the program I use for creating music digitally). Every button can contain a sound which reminded me of the Dutch television program “Zondag met Lubach” in which the host also uses a MIDI pad (a slightly bigger version with more buttons).

Ableton is a very extensive program with a lot of functionalities. If the MIDI pad is used as a soundboard, only a small fraction of the functionalities are used.

That’s why I created a simple WPF application that assigns different sounds to the different buttons of the MIDI pad. I gained experience using the MVVM light library (I was already familair with MVVM).

Bottom line: it was fun to create such application in a short period of time. Besides that, I learned the basics of MIDI input and programming in short increments.

Here’s a quick demo:

