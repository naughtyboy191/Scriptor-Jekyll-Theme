---
layout: post
title: "Try Hackme Vulnversity Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-20
feature_image: images/thm_vulnuni/front.png
tags: [TryHackMe,Port Knocking,Forensics]
published: true
---
<!--more-->
Lets start with the basic nmap scan

![](images/thm_vulnuni/2.png)

This showed that there were 6 ports open on the machine 
ftp was useless as anon login was not allowed 
so the only option was the http website
lets visit the website on port on 3333


![](images/thm_vulnuni/1.png)

This also does not give us anything useful so lets try using gobuster 

![](images/thm_vulnuni/3.png)

We get an interesting directory named **internal** 
lets check it out

![](images/thm_vulnuni/5.png)

So it allows us to upload files to the machine 
lets if we can access the files uploaded by us

Searching for sub-directories inside `internal` directory

![](images/thm_vulnuni/6.png)

So we got the uploads directory 
Lets check it out

![](images/thm_vulnuni/4.png)

so I got my php rev shell listed so lets open up a netcat listner and get the rev-shell

![](images/thm_vulnuni/7.png)

So I got the user flag 

Lets search the suid binaries

![](images/thm_vulnuni/8.png)

On searching for the suid binaries I came across **systemctl** binary,It looked interesting 
On searching systemctl on gtfobins I got this

![](images/thm_vulnuni/9.png)

Lets try getting the root flag using this 

![](images/thm_vulnuni/10.png)

So this was a very straight forward maching no need for any ***crazy*** things

<b><center>Keep Enumerating!!</center></b>