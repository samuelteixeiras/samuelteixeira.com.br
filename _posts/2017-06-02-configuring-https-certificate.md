---
layout: post
title:  "Renew https certificate"
date:   2017-05-02 13:00:00
categories: certbot https linux
---

enew the http certificate with cerbot for nginx
Last year I decided enable https in my server. I am using a digital ocean node and I followed the tutorial: https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04, but I didn't enable the auto renew of the certificate. Why ??

![why](http://i1.kym-cdn.com/entries/icons/original/000/004/006/y-u-no-guy.jpg)

After one year the certificate was experied and this is what you see when you access the page: 

<img src="{{ site.url }}/assets/samuel_page_erro.png" />


My problem was I can run the command in the tutorial [1] to renew because I change the nginx root path to the jekyll root in /var/www/samuelteixeira.com.br/_site.

So to renew the https certificate I have to change the webroot.The command to do this:

{% highlight bash linenos %}
certbot certonly --force-renewal -a webroot -d www.samuelteixeira.com.br -w 
/var/www/samuelteixeira.com.br/_site -d samuelteixeira.com.br

{% endhighlight %}

** Happy day!

[1] sudo certbot certonly --webroot --webroot-path=/var/www/html -d example.com -d www.example.com


Post created with only markdown editor:  http://dillinger.io/
