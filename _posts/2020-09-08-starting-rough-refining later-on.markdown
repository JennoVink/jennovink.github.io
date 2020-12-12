---
layout: post
title:  "Starting rough, refining later on"
date:   2020-08-09 20:00:07
categories: development
description: "The story behind the 34+ million records."
published: true
image: /img/big_data.webp
tags: BigData .NET Optimization
---

Today I got the assignment to 'enrich' data (in Dutch: "dataverrijking"). This means, reading, combining and transforming data into something useful the people of datapreperation can design on a piece of paper.

The desired functionality included reading several large csv files, and based on parameters, reading the according csv (which can contain millions of records), and putting the data back into another database. I started rough and created an initial, naïve implementation to be refine later on. With this method, **it would take 68 hours** to complete the job. Way too long... That's why I kept optimizing my code. My optimalizations include prefetching data from csv & bulk inserting into the database while monitoring the memory to make sure there were no memory leaks. In the end, I reduced the execution time to **less than 7 minutes**.

The final txt file (to be imported by sql server) was a little more than 1.2 GB which took 1:23 minutes to import it into the database.

#### What this says about my coding style
I like using an agile approch. Instead of needing to know every detail upfront, it is sometimes better to just get started see how things works out along the way. Later, optimizations can be implemented on when seeing the whole picture (including details).
