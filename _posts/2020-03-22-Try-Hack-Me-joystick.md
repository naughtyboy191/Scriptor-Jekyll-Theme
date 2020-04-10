---
layout: post
title: "Try Hackme Joystick Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-22
feature_image: images/thm_joystick/front.png
tags: [TryHackMe]
published: true
---
<!--more-->

Let me tell you first the is one of the easiest rooms if you are a beginner on Try Hack ME

Lets start with the nmap scan

![](images/thm_joystick/1.png)

Lets checkout port 80 

![](images/thm_joystick/2.png)

So lets try ftp with username **steve**

![](images/thm_joystick/3.png)

No Success,

LEts try ssh bruteforce using hydra (because ftp bruteforce was taking time 
and I got the user creds for ssh while the ftp one was still running)

![](images/thm_joystick/4.png)

So we go the password and lets login

![](images/thm_joystick/5.png)

So we got our user flag and running linPEAS showed that we had read access to root.txt
so no need for any privesc simply read the flag

![](images/thm_joystick/6.png)

THis room was completed in mere 15 minutes so I couldn't believe myself but it is what it is 

Another one completed 

<b><center>Happy Hacking!!</center></b>