---
layout: post
title: Introduction to Crawling
description: "What would be the best way to crawl. Find the answer near the end of the my lecture !"
modified: 2015-08-21
category: Tech Post
tags: [Scrapy, Python, Web-Crawling ]
imagefeature: cover6.jpg
comments: true
share: true
---


So, recently we needed some data from Indian biggies like housing.com, cardekho.com, olx.com, blah blah... What we wished to do with the data is classified (ask our client if you don't believe me) but I can safely talk about how we got that data. 


Different sites have different kinds of data (like you didn't know that you'd say). CarDekho has listing of old cards up for resale, housing.com has property listings. Furthermore, there are sub-divisions too. What types of cars ? What types of houses ? They are listed under different budgets, age etc. 

There are many ways you could use to scrap data. Let's list the top things that come to mind. 

###Brute force pen and paper

This is a method now isn't it ? Hire 500 people and ask them to visit each page, write down each required detail and you are done. This method is not feasible for obvious reasons. Obvious yes, but let's discuss them to provide the build-up that Scrapy deserves. 

_______
* Too many humans required

This is a problem because humans get tired, make mistakes, are inefficient and most importantly demand salaries.

_________
* Not fast

This is very slow. By the time you will have managed to copy 100 entries to your word doc, many more would have been uploaded.

_________
* Not scalable

If you are done with say all housing.com entries for Mumbai (phew!) and now the client calls and asks Delhi too; you are back to square one.

_________
* It's lame

Imagine a visitor coming to your office and looks at all the people Ctrl-C-ing and Ctrl-V-ing. Looks bad, no ?

~~~~~~~~~~~~~

###Selenium WebDriver

Now this is just as worse to be honest. Selenium helps you automate the browser. Imagine an invisible human opening links, copying the text you programmed it to and pasting it in a Word Doc. Sounds interesting ? It is not. Here's why :


_______
* Harsh on the host

We are responsible users aren't we ? Automating the browser to visit the site thousands of times means sending many many requests to the host's server; all for content we don't need. What we need for example from cardekho.com is : name of the car, age of the car, km traveled by the car, price of the car. We do not care for the pictures, the recommendations that load alongwith that entry, all other makeup the paper has to make it look pretty. We risk getting our IP blocked too if we manage to annoy the host too much.

_______
* Too slow

Selenium opens the webpage and waits for it to load. This takes time. Does't matter if you have the fastest connection, it takes finite miliseconds which could have been avoided. 

_______
* Inefficient

So, we are using a lot of data, are troubling our host by asking for information we don't need, and are waiting longer than we need to for our data. That can be classified as inefficient if you ask me. 



###Use python libs

Now we are talking ! You can bundle together a working solution selecting your favourite from the plethora of python libraries. Say, you can use requests, or httpie, or curl, or wget to get the url, then parse the HTML using beautifulsoup, lxml, HTMLParse, html5lib etc. This will work. But again; here are some drawbacks I thought up :

_______
* Needs some work

You will have to download the libs, get familiar with their APIs, write entire scripts orcherastrating their duties from scratch. This can be done but resolving errors will be need some attention. Also, there could be possible bottlenecks to performance since this is a hand-stiched solution. 

_______
* Not elegant

Okay, now I am just sulking but the solution is not really elegant. It is like you are given two choices. Either you are given all the components (engine, tyres, seats ; you get it) and asked to make a car for yourself or you can just take the cherry red Ferrari and drive away. I agree, I agree, veterans would love to craft their own cars and mix and match; put Hummer engines with Ferrari tyres and play around; but such solutions aren't the most efficient sometimes. 

So. What is the solution you ask ?


##Meet Scrapy

So, scrapy is the Ferrari you would know of if you were reading. It is built by hundereds of dedicated developers specificly for the task of crawling. It has many features built-in which make it fast, efficient (finally !) and easy to use. Writing crawler jobs is as simple as saying what fields you want and from what websites and where to find them. That's it.

I'll write a demo next time, I promise.