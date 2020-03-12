---
layout: post
title: Try Hackme BoilerCTF Walkthrough
description: "Just a simple walkthrough"
date: 2020-03-12
feature_image: images/thm_boilerctf/front.png
tags: [TryHackMe]

---
<!--more-->
So I am back with another writup
this is the [link](https://tryhackme.com/room/boilerctf2)

I started with a quick scan with nmap and got this
![](images/thm_boilerctf/1.png)

The ports open are **21,80,10000**

So we checkout the http page on port 80

![](images/thm_boilerctf/2.png)

It doesn't contain anything useful lets check port 10000
it uses ssl so make sure to use **https:** instead of **http:**

![](images/thm_boilerctf/3.png)

I searched for vulnerability related to this Webmin version But I didn't find anthing useful so 
there is a question related to finding the service on the highest port so I ran a quick scan(it still took 10 mins) for the higher ports and found a port open

![](images/thm_boilerctf/4.png)

On looking deeper into the port I find that ssh is running at this port so 
we have to find ssh creds 

![](images/thm_boilerctf/5.png)

I forgot to look at ftp port so lets see if anonymous login is possible

![](images/thm_boilerctf/6.png)

yes and we find a file lets read it ,It look like a caesar cipher using an online tool I got the message

![](images/thm_boilerctf/7.png)

Very encouraging words in the message ,at this time I had no clue how to get the login creds so I ran the gobuster for hidden directories

![](images/thm_boilerctf/8.png)

So the server is using  **Joomla** CMS
Again running gobuster on the joomla directory

![](images/thm_boilerctf/12.png)

Visiting some of the pages its some cipher its just there to troll me 
I was frustated to see the message I got after visiting some of the pages 
so I didn't share the message in them

![](images/thm_boilerctf/9.png)

![](images/thm_boilerctf/10.png)

![](images/thm_boilerctf/11.png)

On checking *_test* i got the following page

![](images/thm_boilerctf/13.png)

searching for vulnerablity related to it I got [this](https://www.exploit-db.com/exploits/47204)
So it seems that there is RCE in the url so lets see the log file if we can 

![](images/thm_boilerctf/14.png)


So we find some creds 

```basterd:superduperp@$$```

lets login !!

We can find the pass word for stoner 

![](images/thm_boilerctf/15.png)

lets see what is there in stoner's home directory
there is the user.txt flag for us but its name in the machine is secret

![](images/thm_boilerctf/16.png)

lets find the location of root.txt
we find the location at /root/root.txt

lets try if we can exploit find first 
and we can so we use the following command to get the flag
```find / -exec cat /root/root.txt \;```

you will have to stop the command or it will continue till the infinity

![](images/thm_boilerctf/17.png)

So this is the final flag
Hope you learnt something! **:)**