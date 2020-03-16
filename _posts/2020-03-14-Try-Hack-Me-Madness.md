---
layout: post
title: "Try Hackme Madness Walkthrough"
description: "Just a simple Walkthrough"
date: 2020-03-14
feature_image: images/thm_madness/front.png
tags: [TryHackMe]
published: true
---
<!--more-->

First of all as we know its nmap scan as always

![](images/thm_madness/3.png)

so we have ports 22,80 open ;lets check the website

![](images/thm_madness/2.png)

we can see a not loadable image lets view that image

![](images/thm_madness/4.png)

lets download and check its hex 

![](images/thm_madness/5.png)

as you can see why there is a png header in jpg image so lets repair and view the image

![](images/thm_madness/6.png)

we get a hidden directory lets acesss it 

![](images/thm_madness/7.png)

lets check the source 

![](images/thm_madness/8.png)

so we have to brute-force the secret so I wrote a short python script to do this
```python
import requests


url ="http://10.10.188.51/th1s_1s_h1dd3n/?secret="

for i in range(0,100):
	response=requests.get(url+str(i))
	
	if("That is wrong!" in response.text):
		print(i)
		continue
	else:
		print("correct secret :",i)
		break

``` 
this gave me the correct secret as 73

![](images/thm_madness/9.png)

I tried bruteforcing the ssh with hydra using the the string given above but it was already written above that this is not the username 
***such a fool***
so now I tried to steghide the image given on the challenge page  

![](images/thm_madness/1.png)

Yupp this gave me the password without any passphrase

So I tried to extract the thm.jpg file also without any passphrase
but did not get anything

![](images/thm_madness/10.png)

now with the passphrase we got by entering the secret
it got me a username

![](images/thm_madness/11.png)

but as it was given in the hint 
its ROTen so trying rot13 gives the user

![](images/thm_madness/12.png)

Lets login and get the user flag first

![](images/thm_madness/13.png)

Now lets search for SUID binaries
we got this result

![](images/thm_madness/15.png)

Now the screen-4.5.0 looks interesting 
Using my GOOGLE_FU skills I got this vulnerability

![](images/thm_madness/16.png)

lets copy this script to /tmp directory and run it
we got the flag 

![](images/thm_madness/14.png)


<b><center>Happy Hacking!!</center></b>