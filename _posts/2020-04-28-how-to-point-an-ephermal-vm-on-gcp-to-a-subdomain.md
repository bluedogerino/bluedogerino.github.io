---
layout: post
title:  "How to point an ephermal VM on Google Cloud Platform to a subdomain"
categories: tutorial cloud
img: GA1pr7V.png
---

I have made this tutorial for people who don't wish to pay for a static IP from Google,
but still wish to have an easy way to access their server via a subdomain on their domain.
If you are looking for something of the sort, you have come to the right place.
note: I am using CloudFlare DNS , but im sure this can apply to most domain registars.
Let's get started!


1.Firstly create a subdomain on https://ddns.pboehm.de/
------
![dns](https://i.imgur.com/GA1pr7V.png)
 
2.Do ```sudo crontab -e``` in the SSH of your Google Cloud VM
------
![terminal](https://i.imgur.com/0NlhEsG.png)

3.Scroll to the bottom of the file and write ```@reboot``` then copy the command you got from the DDNS until it looks similar to this:
------
![terminal2](https://i.imgur.com/N33y0Gf.png)

4.To close the terminal do Ctrl+C and press y
------
![terminal3](https://i.imgur.com/Ih8R4IW.png)

5.Next, go visit your domain that you registered, my server uses Nginx , so that is what will show up when i visit my own subdomain.
------
![website](https://i.imgur.com/LcQmZFX.png)

6.After confirming that it is your server, let's head to Cloudflare DNS
------
As my use for the server is to use it for ssh, I created a subdomain entry in Cloudflare named ssh.
To do this, I selected CNAME as the type of entry, and in the target enter the domain you got from the DDNS,
in the name entry whatever you want your subdomain to be, and disable the cloudflare proxy status for faster IP adress changes.
It should look something like this:
![cloudflare](https://i.imgur.com/F8EopZ0.png)
After it looks like something above, click Save, and you are done!

7.Check if the subdomain redirects properly to your Google Cloud VM
------
![final](https://i.imgur.com/fMkTn60.png)
If it redirects properly you should be able to see the same site on both domains.

That's it, thank you for reading. :D

