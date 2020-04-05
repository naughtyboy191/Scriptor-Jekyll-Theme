---
layout: post
title: "Try Hackme Knock-Knock Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-18
feature_image: images/thm_knock/front.png
tags: [TryHackMe,Port Knocking,Forensics]
published: true
---

<!--more-->
Nmap scan results show nothing peculiar to explain

![](images/thm_knock/2.png)

lets visit the webpage and download the pcap 

![](images/thm_knock/1.png)

![](images/thm_knock/9.png)

the above screenshot show the order in which port were knocked so lets use the port knocker [script](https://github.com/grongor/knock)

now lets knock the ports in order shown and telnet the last port

![](images/thm_knock/3.png)

we get a hidden directory lets access the directory and download the 2nd pcap file 

![](images/thm_knock/4.png)

On following one of the tcp streams in the pcap file I find this 
looks like some kind of foreign language 

![](images/thm_knock/5.png)

It translates to 1 3 3 7 
so this must be the ports to knock

![](images/thm_knock/6.png)

we get another hidden directory so lets check it 
seem like base64 lets check

![](images/thm_knock/7.png)

So it gives us the ports to knock and then ssh

![](images/thm_knock/8.png)

we get the username password lets login

but as soon as we login the system logs us out

![](images/thm_knock/10.png)

so lets try the same command with `/bin/bash` in additon to it as we get the shell

![](images/thm_knock/11.png)

lets stabilise it using tty
and `sudo -l` to check the permissions 

![](images/thm_knock/12.png)

so the system name looked suspicious 
so I looked into it and found that the linux version is outdated and vulnerable so 
I checked for it online

![](images/thm_knock/13.png)

so we have to compile the code on the machine so I transferred the ofs.c to the box using scp and compiled it to get the binary and then ran it to get the root shell

![](images/thm_knock/14.png)

So nice box !
My first kernel exploit so it was great getting the root shell without any roadblocks<br>

<b><center>Happy Hacking!!</center></b>