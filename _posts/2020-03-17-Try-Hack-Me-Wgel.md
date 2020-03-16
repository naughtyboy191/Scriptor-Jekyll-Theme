---
layout: post
title: "Try Hackme Wgel Walkthrough"
description: "Just a Wgel Walkthrough"
date: 2020-03-17
feature_image: images/thm_wgel/front.png
tags: [TryHackMe]
published: true
---

<!--more-->
Nmap Scan Results:-

![](images/thm_wgel/2.png)

Nothing interesting in the nmap scan lets check out the http page

![](images/thm_wgel/1.png)

On checking the source of index.html we get this

![](images/thm_wgel/3.png)

So Jessie is a user for this box
Nice ,A thing to **remember**
Lets start with gobuster enumeration

![](images/thm_wgel/4.png)

Sitemap directory seems interesting
lets check it out 

![](images/thm_wgel/5.png)

Doesn't give any special information 
so lets recursive scan into the sitemap directory 

![](images/thm_wgel/6.png)

<b>Interesting!!</b>
we find a .ssh directory 
On checking it out we get a rsa key
Lets check wether this key has any password or not??

![](images/thm_wgel/7.png)

Lets quickly change the permissions of the rsa key and login!!

![](images/thm_wgel/8.png)

We get the user flag 
lets check `sudo -l`
so we can run `wget` as root nice checking for wget priv-esc we can easily find so many exploits
I used this --

![](images/thm_wgel/10.png)

Lets HAck~~~

![](images/thm_wgel/9.png)

SO that's it we get the root flag as well
easy box nothing much to explain here!!<br>
Remember always !!

<b><center>Enumeration Is The Key!!</center></b>