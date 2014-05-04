---
author: Simon
comments: true
date: 2011-03-31 17:53:54+00:00
layout: post
slug: quick-trick-to-view-mobile-versions-of-web-sites-using-chome-on-os-x
title: Quick Trick to View Mobile Versions of Web Sites Using Chome on OS X
wordpress_id: 235
categories:
- Development
tags:
- mobile
- trick
---

The other night I attended a talk by Google's [Steven Souders](http://twitter.com/souders), a web performance expert (and creator of [YSlow](http://developer.yahoo.com/yslow/)).  He's now almost exclusively focused on mobile performance, and he shared a little trick to view mobile sites on the desktop, and I thought I'd share exact steps on how to do that on OS X as I used it today.

For browsing I use [Chrome](http://www.google.com/chrome/intl/en/landing_chrome_mac.html?hl=en) as it's incredibly fast and based on [webkit](http://www.webkit.org/), the rendering engine inside Mobile Safari (iphone) and the Android Browser. While Firefox has some [great tools](https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher/) that allow you to change the user-agent string, which is how most sites detect which version of the site to render, Chrome doesn't have any easy-to-use extensions.

You can, however, change it from the command line when you launch the browser. To do this, close any open windows of Chrome and launch the following from the command line. 

For Android I used the user-agent string from my HTC Evo:
`/Applications/Google Chrome.app/Contents/MacOS/Google Chrome -user-agent="Mozilla/5.0 (Linux; U; Android 2.2; en-us; Sprint APA9292KT Build/FRF91) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1"`

For the iPhone I used one for the iPhone 4:
`/Applications/Google Chrome.app/Contents/MacOS/Google Chrome -user-agent="Mozilla/5.0 (iPhone; U; CPU iPhone OS 4_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7"`

and for the iPad I used the one from my iPad:
`/Applications/Google Chrome.app/Contents/MacOS/Google Chrome -user-agent="Mozilla/5.0 (iPad; U; CPU OS 4_2_1 like Mac OS X; en-us) AppleWebKit/533.17.9 (KHTML, like Gecko) Version/5.0.2 Mobile/8C148 Safari/6533.18.5"`

To see the difference take a look at google.com with normal Chrome vs. with the Android user-agent:


Mobile (Android)

![](http://www.liquidrhymes.com/wp-content/uploads/2011/03/Screen-shot-2011-03-31-at-10.43.41-AM-300x222.png)




Desktop

![](http://www.liquidrhymes.com/wp-content/uploads/2011/03/Screen-shot-2011-03-31-at-10.46.04-AM-300x222.png)



