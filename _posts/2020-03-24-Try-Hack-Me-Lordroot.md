---
layout: post
title: "Try Hackme Lord of the Root Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-23
feature_image: images/thm_lordroot/front.png
tags: [TryHackMe]
published: true
---
<!--more-->

Lets start with the nmap scan 

![](images/thm_lordroot/1.png)

accessing 1337 dosn't give us anything 
lets try accessing ssh as any random user

![](images/thm_lordroot/2.png)
SO it looks like we need to knock the port to access the 1337 port 
use any knock script from github to do this 
I am not showing that 

Lets look at the newly opened 1337 port

![](images/thm_lordroot/3.png)

I knew that there would be a directory named **mordor** as this machine was related to lord of the rings on accessing it I got a base64 strings lets decode it

I know this is kind of random but sometimes **reading books** helps you :)

you can always find the directories using gobuster

![](images/thm_lordroot/5.png)

the source:-

![](images/thm_lordroot/4.png)

![](images/thm_lordroot/7.png)

So its a hidden php login form ,capture the login request and use sqlmap to get the user creds

![](images/thm_lordroot/8.png)

by using hit and trial we get login success with smeagol

![](images/thm_lordroot/9.png)

DOing some recon we see that the linux version is very old there must be some vulnerability related to it
so exploitdb gives us the vulnerability which can be used to escalate permissions to root so 
lets compile and run the exploit to get the flag

![](images/thm_lordroot/10.png)

THis room was solved due to a bit of luck bit it was fun 
there are other ways of escalating privilages if you want that plz comment below


<b><center>Happy Hacking!!</center></b>