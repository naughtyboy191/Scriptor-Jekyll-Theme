---
layout: post
title: "Try Hackme Willow Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-16
feature_image: images/thm_willow/front.png
tags: [TryHackMe, Forensics]
published: true
---
<!--more-->

Lets start with the nmap scan on the machine we can see that three ports are open
namely ssh ,http ,nfs

![](images/thm_willow/2.png)

lets checkout the http port we get this

![](images/thm_willow/11.png)

Lets decode it using cyberchef

![](images/thm_willow/12.png)

so we are given the ssh login key in numerical form which can be converted to actual key if we know the private key and public exponent

lets checkout the nfs port

![](images/thm_willow/1.png)

So we get the private key and modulus

so we can write a quick python script like this to get the ssh private key

```python
priv=61527
pub=37627

with open("ssh_raw", "r") as raw_text:
    data = [int(i.strip("\n")) for i in raw_text.read().split(" ")]

for i in data:
	print(chr(i**priv%pub),end="")
```

![](images/thm_willow/3.png)

saving the key and brutforcing its password using ssh2john

![](images/thm_willow/4.png)

we get the password 
lets login!!

![](images/thm_willow/6.png)


lets copy the user.jpg to our local system

![](images/thm_willow/5.png)

it contains our user flag 

![](images/thm_willow/7.png)

lets continue with further enumeration 
the command `sudo -l` give us the following results 

![](images/thm_willow/8.png)

So we can use mount as root so we mount the `hidden_backup` folder to `/mnt/creds` directory and view the contents

After priv-esc to root we check root.txt 
so it give us this 

![](images/thm_willow/9.png)

So it clocked that there maybe a file hidden in user.jpg image as said in root.txt so lets use the root password as passphrase and yup we got the flag

![](images/thm_willow/10.png)

Nice Box , Had lot of fun while figuring out the root flag 

<b><center>Happy Hacking!!</center></b>