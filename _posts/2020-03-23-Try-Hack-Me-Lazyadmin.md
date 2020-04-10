---
layout: post
title: "Try Hackme LazyAdmin Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-23
feature_image: images/thm_lazyadmin/front.png
tags: [TryHackMe]
published: true
---
<!--more-->

So lets nmap scan the IP 

![](images/thm_lazyadmin/1.png)

Nothing peculiar lets try gobuster for hidden directories

![](images/thm_lazyadmin/2.png)

SO the **content** directory seems interesting lets check it out

![](images/thm_lazyadmin/3.png)

So it looks like the machine is running sweetRice CMS
lets enumerate the content directory using gobuster

![](images/thm_lazyadmin/4.png)

The **inc** directory seemed interesting 
on accessing it there was a folder named mysql backup present there so lets
view its contents

![](images/thm_lazyadmin/5.png)


![](images/thm_lazyadmin/6.png)

So we get the admin credentials in the mysql backup file

![](images/thm_lazyadmin/7.png)

the hash was cracked easily using crackstation

![](images/thm_lazyadmin/8.png)

lets login into the cms and see what can be useful

![](images/thm_lazyadmin/9.png)

on searching through web for rce in the cms it seemed that we can publish  ads
So we used the php-revshell and posted the ad online

![](images/thm_lazyadmin/10.png)

the uploaded file can be accessed from the inc folder so we access it and get the shell

![](images/thm_lazyadmin/11.png)

we get the user flag from the home folder

![](images/thm_lazyadmin/12.png)

So on checking for sudoers we get that we can use perl as root

![](images/thm_lazyadmin/13.png)

So i changed copy.sh to spawn a reverse shell(use pentestmonkey for help)
and execute the perl script as root and got the root shell and found the root flag 

![](images/thm_lazyadmin/14.png)

We can also user other ways but this was the way I used to get root 

<b><center>Keep Enumerating!!</center></b>
