---
layout: post
title: "Try Hackme Cherry Blossom Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-21
feature_image: images/thm_cherry/front.png
tags: [TryHackMe, Hash_cracking]
published: true
---
<!--more-->

Nmap scan as usual

![](images/thm_cherry/1.png)

Seeing port 445 open means that it must be SAMBA!!
lets use enum4linux
ANd yes there is an open share on the smb server

![](images/thm_cherry/2.png)

Lets access the share using smbclient

![](images/thm_cherry/3.png)

We got a text file ,it had a base64 encoded string so copying the contents of the journal.txt file into new file after base64 decoding
it turns out to be a png file after checking out many tools I finally got a zip file using **stegpy**

![](images/thm_cherry/4.png)

WHile trying to unzip the zip it showed that it was corrupted so after 
getting the file headers correct and trying to unzip for the file it asked for password 

![](images/thm_cherry/5.png)

I know many people like to use fcrackzip for password cracking but I love JohnTheRipper its da best 
And almost instantly I got the password

![](images/thm_cherry/6.png)

after unzipping the zip I got a ctz file I knew that it was a Cherry tree document but when I used cherry tree to open the file it asked for password 
A quick google search on cracking ctz file password gave us that we need to use `7ztojohn` for password cracking

![](images/thm_cherry/7.png)

Viewing the contents of the document we got the first flag as well as 
the wordlist to use for ssh bruteforce

![](images/thm_cherry/8.png)

![](images/thm_cherry/13.png)

![](images/thm_cherry/9.png)

LEts quickly merge all the worlists into a new file and get to the bruteforce

![](images/thm_cherry/10.png)

SO we got the creds using hydra

![](images/thm_cherry/11.png)
lets login 
It seems that there are two users on the machine and Johan is the the person who wrote the diary as **J**

![](images/thm_cherry/12.png)

using linPEAS I got to know about a backup file 
on checking it out it turns out to be backup of shadow file
SO we get the hash for johan user
![](images/thm_cherry/14.png)

Lets use john as always but make sure to use the wordlist that we made earlier not the great **rockyou.txt**,It might blow up your computer due to the load,LOL

![](images/thm_cherry/15.png)

Lets login 
I forgot to get the user flag first lets take it 

![](images/thm_cherry/16.png)

when I used sudo -l the password was shown as asterisks on the screen,seems that its a sudo vulnerablity 
I will leave that on you to find out the exploit for this vulnerablity

lets run the exploit and get the root

**EZ PZ**

![](images/thm_cherry/17.png)

So this was one of the most time-consuming boxes on tryhackme that I have solved
Its was a great feeling when I cracked anything using JOhn 

Anyways,

<b><center>Happy Hacking!!</center></b>