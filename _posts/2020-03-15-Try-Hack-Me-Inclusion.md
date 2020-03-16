---
layout: post
title: "Try Hackme Inclusion Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-15
feature_image: images/thm_inclusion/front.png
tags: [TryHackMe, LFI]
published: true
---
<!--more-->
Basic nmap scan as always 

![](images/thm_inclusion/5.png)
Open ports are 22,80
Nothing interesting here 
lets checkout the website

![](images/thm_inclusion/1.png)

Here lets checkout LFI-Attack because **obviously**

![](images/thm_inclusion/3.png)

So I think it is reading the lfiattack named file
so lets change the file to /etc/passwd

![](images/thm_inclusion/4.png)

we get the credentials as a comment so lets 
login

![](images/thm_inclusion/6.png)

so we got the user flag 
and we can run the socat as root
so lets checkout GTFObins for socat

![](images/thm_inclusion/7.png)

lets configure the env variable and keep the port listening on our machine

![](images/thm_inclusion/8.png)

so on running the socat on our terminal I get the root terminal 

![](images/thm_inclusion/9.png)

So we got the root on the machine and the flag

That's all and Remeber

<b><center>Enumeration Is The Key!!</center></b>
