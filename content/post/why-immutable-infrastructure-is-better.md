+++
author = "Darshan Chaudhary"
date = 2019-03-06
title = "Infrastructure should be immutable"
+++


## Introduction

Infrastructure is the hardware that runs the software of any company. It can be a physical data center owned and operated by the company or virtual machines rented on a public cloud. 

The entire pipeline of getting the software from the developer's machine to the server is the deployment pipeline, but what this blog focuses on is why that process should end with immutable infrastructure. 

Immutable infrastructure is when you can only do 2 operations on it. Either bring it up or take it down. You are not allowed to go in and update or modify it. Let's talk about an example service `foobar`, which is deployed on 10 machines in production. 

If it is deployed barebones, one could go in and change the config of the program and restart it for example. However, if it is immutable, to change it, you would have to stop the server, start a new one and deploy the updated service on it. 


There are several advantages to doing this:

  * Avoiding snowflake servers
  
    * These are servers that look similar on the surface but actually have many small differences, like different users on them, different config for the program etc
    
    * This can also be the case that someone `ssh`es and makes a hotfix and then forgets to check that change in the source code, so only that server is different now
    
    
  * Declarative provisioning
  
    * You don't need to specify how to move from state A to state B if you use immutable infrastructure. You can just say, I want state B and the old infrastructure is destroyed and the new one is provisioned. 
    
    * This solves a whole class of problems related to complex migration between states that needs to be explicitly coded otherwise
    
    
  * Easy upgrades and rollbacks
  
    * Immutable infrastructure makes it easy to upgrade from version 1 to version 2, since it is just a matter of destroying the old machines and getting the new ones on. Rollbacks are simple likewise.
    


So, infrastructure is best immutable, and the way to achieve that is docker and kubernetes!
