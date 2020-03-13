---
layout: post
title: "Try Hackme Mr Robot CTF Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-13
feature_image: images/thm_mr_robot/front.png
tags: [TryHackMe]
---

So we start with basic enumeration

![](images/thm_mr_robot/1.png)

So ports 80,443 is open nothing special here lets check the site

![](images/thm_mr_robot/2.png)



nothing to find here to lets check the robots.txt file

![](images/thm_mr_robot/3.png)

yup there is the first flag for us
lets get it 
![](images/thm_mr_robot/15.png)

now we download the dictionary file 
running nikto

![](images/thm_mr_robot/7.png)

Nothing interesting here as well,now on running gobuster we got that it has Wordpress CMS so lets try for wp-login.php page 

![](images/thm_mr_robot/4.png)

yup its there lets check for username from the dictionary 
it was elliot kind of guessed it before

![](images/thm_mr_robot/6.png)

now using burp to capture the requests and use hydra

![](images/thm_mr_robot/5.png)

Since the dictionary had lot of duplicates I used used uniq command to make new dictionary so number of tries we have to do be less

![](images/thm_mr_robot/16.png)


lets login using the found pass we get the dashboard

![](images/thm_mr_robot/8.png)

Lets check the editor ,we can edit the 404.php to get php rev-shell lets change the contents of 404.php and get the shell

![](images/thm_mr_robot/10.png)

Stabilising the shell using python

![](images/thm_mr_robot/9.png)

Couldn't read the key but got the md5 hash of the user lets crack it online

![](images/thm_mr_robot/11.png)

Lets login and get key 2

![](images/thm_mr_robot/12.png)


now checking for vulnerable binaries got nmap 
![](images/thm_mr_robot/13.png)

using nmap --interactive to get the shell
as the nmap version being used is very old

![](images/thm_mr_robot/14.png)

got the key 3 as well was a good box learnt about how to use nmap vulnerability 


<b><center>Happy Hacking</center></b>
