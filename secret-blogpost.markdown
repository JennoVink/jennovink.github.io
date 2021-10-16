---
layout: post
title: "Secret blogpost"
description: "A secret blogpost with a small poc."
date: 2021-10-14 20:00:00
hero_image: /img/pluralsight-badge.svg
hero_height: is-small
hero_darken: true
image: /img/pluralsight-badge.svg
published: true
author: Jenno
tags: PoC
---

## You've found a secret blogpost😀

I red [this blogpost](https://infosecwriteups.com/how-i-am-able-to-hijack-you-1cab793a01d1){:target="_blank"} and I decided to give it a try my self.

Watch this gif and go to [google.com](https://www.google.com) and type ```Jenno```.

<iframe width="100%" height="300" src="//jsfiddle.net/rnhg2ysm/show/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

Note that in the PoC above, you have to press the button 'Run this fiddle'. In the example of the blogpost that wasn't needed (maybe by using embed.ly?).

I still haven't found out a way to not show the 'run this fiddle' button. I tried plain html and js, but then you aren't logged it at google by default. Only the results are show. For this to work, you need to be logged in in google. Fortunately, this is a good thing, or else everyone could exploit this easily.