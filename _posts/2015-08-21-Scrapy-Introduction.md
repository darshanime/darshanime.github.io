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


Recently, I needed some data from big Indian biggies like [housing.com](https://housing.com/){:target="_blank"}, [cardekho.com](http://www.cardekho.com/){:target="_blank"}, [olx.com](http://olx.in/?from=www){:target="_blank"} and others for a personal project. What exactly it is too early to say but we can talk about how I got the data. 


Different sites have different kinds of data stored in different ways. CarDekho has second hand cars up for resale, housing.com has properties. Furthermore, there are sub-divisions too. What types of cars ? What types of houses ? They are listed under different headings. 

There are many ways one can use to scrap data. Let's list the top things that come to mind. 

_______

###Brute force pen and paper

This is a method now, isn't it ? Hire 500 people and ask them to visit each page, write down all the required details and you are done. This method is not feasible for obvious reasons. Obvious yes, but let's discuss them to provide the build-up that Scrapy deserves. 


* **Too many humans required**

This is a problem because humans get tired, make mistakes, are inefficient and demand salaries.


* **Not fast**

This is very slow. By the time you will have managed to copy 100 entries to your word doc, many more would have been uploaded.


* **Not scalable**

If you are done with say all housing.com entries for apartments up for Renting in Mumbai (phew!) and now the client calls and asks for Delhi too; you are back to square one.


_______

###Selenium WebDriver

Now this is just as worse to be honest. Selenium helps you automate the browser. Imagine an invisible human opening links, copying the text you programmed it to and pasting it in a Word Doc. Sounds interesting ? It is not. Here's why :


* Harsh on the host

We are responsible users aren't we ? Automating the browser to visit the site thousands of times means flushing the host's server with many many requests; all for content we don't need. What we need for example from cardekho.com are certain specific details about the car like : name, age, km traveled, price etc. We do not care for the recommendations that load along with that entry, the pop-up asking us to sign in/sign up and all the other makeup the page has to make it look pretty. We risk getting our IP blocked too if we manage to annoy the host too much.


* Too slow

Selenium opens the web-page and waits for it to load. This takes time. Doesn't matter if you have the fastest connection, it takes finite milliseconds which could have been avoided. 


* Expensive

We will have to purchase a high-bandwidth connection from the ISP and consume a lot of data (because we will be opening thousands of pages). You might consider taking things to the cloud for the much needed speed-up but then again, charges. 

_______

###Use python libs

Now we are talking ! You can bundle together a working solution by selecting your favorites from the plethora of python libraries. Say, you can use requests, or httpie, or curl, or wget to get the url's HTML, then parse it using beautifulsoup, lxml, HTMLParse, html5lib etc. This will work. But again, here are some drawbacks I thought up :


* Needs some work

You will have to download the libs, get familiar with their APIs and write entire scripts orchestrating their duties from scratch. This can be done but resolving errors will be need some attention. Also, there could be possible bottlenecks to performance since this is a hand-stitched solution. 


* Not elegant

Okay, now I am just sulking but the solution is not really elegant. It is like you are given two choices. Either you are given all the components (engine, tires, seats) and asked to bundle a car for yourself OR you can just take the cherry red Ferrari and drive away. I agree, veterans would love to craft their own cars and mix & match; put Hummer engine with Ferrari tires and play around. But often such solutions aren't the most efficient. 

So. What is the solution you ask ?

##Meet Scrapy
<br>
Scrapy is the Ferrari in the above situation. It is built by hundreds of dedicated developers specifically for the task of crawling. It has many features built-in which make it fast, efficient (finally !) and easy to use. Writing crawler jobs is as simple as saying what fields you want, from what websites and where to find them. That's it.

I'll write a demo next time, I promise.


<div class="comments">
        <div id="disqus_thread"></div>
        <script type="text/javascript">
            /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
            var disqus_shortname = "darshanime"; // required: replace example with your forum shortname

            /* * * DON'T EDIT BELOW THIS LINE * * */
            (function() {
                var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
                dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
                (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
            })();
        </script>
        <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
        <a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
    </div>

<div>
    <script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-58520192-1', 'auto');
  ga('send', 'pageview');

</script>
</div>