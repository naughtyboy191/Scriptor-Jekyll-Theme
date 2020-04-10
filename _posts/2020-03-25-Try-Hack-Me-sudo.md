---
layout: post
title: "Try Hackme Sudo room Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-23
feature_image: images/thm_sudo/front.png
tags: [TryHackMe]
published: true
---
<!--more-->

Lets start with the nmap scan

![](images/thm_sudo/1.png)

nothing odd lets access port 80

![](images/thm_sudo/2.png)

looking at the message looks like something to do with user-agent

On trying as **Agent A** I get the following response,I am not going to show you all the alphabet responses,**C** get us something interesting

![](images/thm_sudo/3.png)

lets look at ftp with username chris and blank pass

![](images/thm_sudo/4.png)

lets take a look at the files we have got

![](images/thm_sudo/6.png)

SO after reading the note its sure that its a steganography problem
very easy ,you just gotta know the right tools

![](images/thm_sudo/7.png)

lets crack the 7z with john

![](images/thm_sudo/8.png)

on reading the message ot seemed like base64 

![](images/thm_sudo/9.png)

What to do with "Area51", then i remembered that we have a jpeg image as well lets try steghide and we get the user password

![](images/thm_sudo/10.png)

I also cracked the password for chris but it was not needed 

![](images/thm_sudo/5.png)

checking the home directory of chris gave us nothing but a ugly photo of some alien
lets login as james and get the user flag

![](images/thm_sudo/11.png)

the sudoers file had interesting stuff looking at the google gets us a priv esc vulnerability

![](images/thm_sudo/12.png)

Exploit Db:- 

![](images/thm_sudo/13.png)

so lets privesc and get the flag!!
![](images/thm_sudo/14.png)

It was one of the easy privesc as nothing to change just one line of code

<b><center>Keep Enumerating!!</center></b>