---
author: Simon
comments: true
date: 2010-07-21 06:05:26+00:00
layout: post
slug: these-are-a-few-of-my-favorite-startup-tools-part-1-frameworks-platforms-and-hosting
title: 'These are A Few of My Favorite Startup Tools: Part 1 - Frameworks, Platforms,
  and Hosting'
wordpress_id: 110
categories:
- Development
- Technology
---

![tool kit](http://farm4.static.flickr.com/3627/3315718996_a89ec57de4.jpg)



Photo by [ian_munroe](http://www.flickr.com/photos/ian_munroe)


  


In the past couple years I've been working for/on startups I've found that the world of internet development had changed fairly substantially since the time I seriously coded for work. 

When I graduated from college in 1999 I went to work for an ecommerce company called [SelfCare.com](http://www.selfcare.com/) (we were going to be the Amazon of wellness products), and I was working in Microsoft's [Active Service Pages](http://en.wikipedia.org/wiki/Active_Server_Pages) (ASP). No, not [ASP.NET](http://en.wikipedia.org/wiki/ASP.NET), but ASP, with it's (horrendous) [VBScript](http://en.wikipedia.org/wiki/VBScript) language. I left SelfCare a year later (it subsequently went out of business and was purchased for it's assets almost immediately after I left) and worked for Ask Jeeves, where I worked in ASP and then got to lead the charge to ASP.NET (I got to spend some great time up at Microsoft getting the inside scoop on their new platform, which really was a huge step forward). A huge chunk of my coding time was spent trying to make my markup compatible for [Netscape Communicator 4.7](http://en.wikipedia.org/wiki/Netscape#Netscape_Communicator_.28versions_4.0.E2.80.934.8.29), so you know about when this was. A few years later I moved to management, and I really didn't do a whole lot of coding for number of years.

Flash forward to 2009: I'm working at a startup, and I decide to roll up my sleeves and get my hands dirty again. Well, I've found there are a ton of tools, frameworks, and software that make my job as a developer much easier, so I decided to put together as list of them. I'll start with Frameworks, Languages, and Hosting:

**Frameworks and Languages**

I used to write a lot of code by hand to get cross-browser compatibility, but the rise of AJAX frameworks has eliminated those incredibly tedious and laborious tasks. My code used to be very difficult to read as well, with HTML mixed in with scripting:

[html]
  <div><% = request.POST["hello_world"] %></div>
[/html]

Yuck! Thankfully, the [MVC Framework](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) has changed all of that, and I rarely have to embed real code in markup. These frameworks help me do this:





  * **[Python](http://python.org/)** and **[Django](http://www.djangoproject.com/)/[Pylons](http://pylonshq.com/)/[Web.py](http://webpy.org/)/etc.**. The former is a great dynamically typed language with a ton of web support, and the latter are [MVC](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) frameworks for it. Starting with these make your life a hell of a lot easier.



  * **[Ruby on Rails](http://rubyonrails.org/)**. The former (Ruby) is the language, the latter (Rails) is a MVC framework with some [AJAX](http://en.wikipedia.org/wiki/Ajax_(programming)) ([Prototype](http://www.prototypejs.org/)) mixed in. Ruby is very similar to python IMHO, and Rails makes it really easy to develop web apps, but I get nervous about the [ORM](http://en.wikipedia.org/wiki/Object-relational_mapping) in Rail, as I always wonder what it's doing beneath my high level code.



  * **[PHP](http://php.net/)** and **[CakePHP](http://cakephp.org/)**. PHP is the P in LAMP, and is a really popular scripting language. It's pretty limited (doesn't do threads, for example) for some tasks, but it's widely supported and a ton of great open source applications (like [Joomla](http://www.joomla.org/) and [Magento](http://www.magentocommerce.com/)) are written in it. CakePHP is a well supported MVC for PHP.



  * **[jQuery](http://jquery.org/)**. The most [successful AJAX library](http://trends.builtwith.com/javascript/JQuery), and really easy to use. It's hard for me to remember writing DOM manipulation in javascript, but that's what I did before I found jQuery.



  * **[Blueprint CSS Framework](http://www.blueprintcss.org/)**. Implementing layouts can be very time consuming, and in 2010 you definitely do not want to resort to html tables, so it's best to do layouts using CSS positioning. For those of us who aren't CSS experts thankfully there is help - the Blueprint CSS Framework makes your layout life a thousand times better. You can get table like layouts without a ton of work using Blueprint, which is a huge time saver.




**Hosting and Servers**

Cloud computing has taken off the past few years, and you no longer need to buy your own servers to get off the ground and going. 





  * **[Amazon EC2](http://aws.amazon.com/ec2/)**. I probably don't need to explain this one, the best known cloud computing platform allows you to add server capacity at-will (and at-wallet). However, you pretty much need to run your own infrastructure as Amazon only provides base OS images - you'll still need to do system administration on your EC2 instances.



  * **[Media Temple](http://mediatemple.net/)**. I use Media Temple for any PHP hosting needs, and with the $50/mo [dedicated virtual instance](http://www.mediatemple.net/webhosting/dv/) I get root ssh access, which is great. 



  * [**Google App Engine**](http://code.google.com/appengine/). I've been using Google's cloud computing service lot more recently, as it lets you get an application up quickly and for free (you pay as you consume more resources). Differing from Amazon's EC2 in that Google doesn't let you install your own OS and languages (you have to use what they provide), it's great in that it's free (well, it starts that way) and you don't have to do much of your own system administration. App Engine currently supports java and python, and you can run any of the python MVC frameworks on it. I love that I can get a site up in less than a half hour by copying an existing app engine project, editing it, and moving my DNS there.




That's the initial plumbing. I'll talk more in my next post about editors, software tools, and other useful open source software.

