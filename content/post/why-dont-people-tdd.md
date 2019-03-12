+++
author = "Darshan Chaudhary"
date = 2019-03-12
title = "Why wouldn't people TDD"
+++


At the Go-Jek bootcamp, we have been thinking a lot about test driven development and how it leads to fewer bugs and more reliable software. Moreover, it also leads to a higher speed of development. A [recent study](https://www.microsoft.com/en-us/research/blog/exploding-software-engineering-myths/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fnews%2Ffeatures%2Fnagappan-100609.aspx ) from Microsoft concluded:

> Test-driven development has been shown to reduce defect rates 40% to 90%, with an increase in development time in the 15%-35% range.

The same message more or less has also been preached by Ajey Gore, CTO at Go-Jek. [Here](https://www.youtube.com/watch?v=FA0mmD0Y8cI) he is talking about how TDD helps write better software, faster. 

Given all the benefits, I was wondering why it isn't as prevalent as it should be. In my working experience of 2 years, I had never come across any developer who was using this technique to write code. I too never bothered about it and considered it to be not worth the trouble. 

However, I tried it recently when writing Conway's Game Of Life in Ruby, a language I had never written in before and I was surprised at how efficient it made the entire process. Once I had the specs pinned down, I was confident about writing the functionality, and once all was green, I could just continue building on from there, with speed.

It got me thinking, in a regular project, what factors would make a developer _NOT_ adopt test driven development. 


#### Lack of prior experience with it
  
  If one has had not any prior experience with TDD, the act may seem very laborious and not worth the effort, even if the developer knows that it is something good, an ideal to be aimed for.
  It really does take forcing oneself to work with it for a few projects for it to become second nature.
  
  
#### Lack of others in the team following it
  
  TDD is a good practice to follow by one alone irrespective of others in the team, but when pairing with someone, it gets in the way if the other person doesn't seem to invested in it.
  
  
#### Not having a project layout
  
  In my personal experience, since I had the Conway's Game of Life written in Java already, I had the hardwork of thinking about the data structures, control flow thought out already for me and I just had to port the classes etc from Java to Ruby (while respecting the standard conventions in Ruby of course). 
  This coupled with the fact that I was not familiar with the Ruby syntax meant that spending some time writing the spec allowed me to play with the code as much as I wanted, and being confident about the implementation when the specs passed. 
  
  I am not sure how much this matters though, because regardless of having a project layout, I can imagine how using TDD would help you move in any direction you are moving, faster.
  

One thing to note here is that, apart from the notion of TDD adding "overhead", which is a common misconception, there should be no doubt about one's ability to write tests. If you are writing software in that language, you by definition are able to write tests. It just is a matter of getting in the habit and seeing the benefits.

