---
author: Simon
comments: true
date: 2010-09-11 23:50:04+00:00
layout: post
slug: ive-got-5-on-it-why-i-believe-html5-will-supplant-apps-as-the-mobile-applications-of-choice
title: I've Got 5 On It - Why I Believe HTML5 Will Supplant Apps as the Mobile Applications
  of Choice
wordpress_id: 190
categories:
- Development
- Technology
---

![phones](http://farm3.static.flickr.com/2766/4257345088_b198e10c19_z.jpg)


Photo courtesy of [johncatral](http://www.flickr.com/photos/johncatral/)


  

The last few months my co-founder and I have been focused on developing a mobile application, and one of the biggest debates we had was whether we wanted to develop native applications for the iPhone and Android. Our initial perception was that we **needed** to develop a native app, because that's where all the user's are. After doing some more research, however, we decided that we would develop our initial version in HTML5. This post discusses why we made that decision.

First off, a little background about the state of mobile application development. There are two major ways to get your software to user's on a mobile device:



	
  * Build a native application

	
  * Build a web version of your application - in HTML5



**Building Native Apps**

To build native apps you'll need to build a version of your application for each mobile platform. The current dominant mobile platforms are Nokia's Symbian ([widely panned](http://tech.fortune.cnn.com/2010/09/10/gartner-and-idc-plot-androids-meteoric-rise-to-2014/) as not a true "smartphone platform"), Apple's iOS, Google's Android, BlackBerry's BlackBerry OS. In addition, Palm's WebOS may re-emerge as HP purchased them and may invest more in the platform, and Microsoft may roar back on the scene with the launch of [Windows Phone 7](http://en.wikipedia.org/wiki/Windows_Phone_7).

![Smartphone Market Share](http://chart.apis.google.com/chart?chxs=0,676767,0&chxt=x&chs=500x250&cht=p&chco=FFCC33|FFEAC0|E8F4F7|DDF8CC|E5ECF9|E8E8E8&chl=|||||&chdl=Symbian+(Nokia)|Android+(Google)|RIM+(BlackBerry)|iOS+(Apple)|Windows+Mobile+(Microsoft)|Other&chp=0.1&chtt=2010+Worldwide+SmartPhone+OS+Share+(Gartner)&chd=s:YLLJDD)

Looking at that chart we can see we've got 4 major OS platforms to write for (subtracting Windows Mobile as it's not long for the world), and 2 more looming on the horizon (Palm/HP's WebOS, and Microsoft's Windows Phone 7). Is it easy to build for these platforms?




	
  * Symbian applications are written in C++, but some apps are written in Python and Adobe's Flash. Most US app developers ignore Symbian's platform, as it's widely considered a lower-tier smartphone OS

	
  * Android applications are written in Java and written specifically for the OS. Google provides lots of support resources, but do not provide native UI elements for many functions, and thus many applications written for the platform look radically different from one another.

	
  * iOS applications are written in Objective-C, with a native UI library called [Cocoa](http://developer.apple.com/technologies/ios/cocoa-touch.html) providing a lot of the UI elements. Most iOS applications therefore have a very similar UI

	
  * RIM's BlackBerry OS Applications are written in Java



One of the problems with developing for each platform is that there are differences between the devices on each platform. This has yet to become a huge deal, largely because the platforms are only a few years (I always pinch myself to remember: the iPhone launched only 3 years ago, in 2007!) old, but with Android there are differences in the OS versions (everywhere from version 1.5 to today's current 2.2) and in the hardware devices, with iOS there are some running the latest version with multi-tasking and some not, and with BlackBerry some devices have a touchscreen and some do not. As a developer, writing for the different variations can be quite daunting!

In addition to writing across different languages and platforms there is another challenge to writing any kind of native application: installation and distribution. Bear with me a second while I tell an anecdote about applications: I remember my first job, in 1999, when I worked for an e-commerce company named SelfCare.com. For bug-tracking we used an application that the consulting company we hired, Cambridge Technology Partners, had written for us in Visual Basic. This application ran on each developer's desktop and connected to a central server to pull down the data on the individual bugs. This worked fairly well, except when we had to fix a problem with the desktop software. The application's developer would fire up his IDE, fix the problem, and then send out a mass email with an attached executable with the new software. Some people would inevitably not install, and would therefore be running old versions of the software with outdated features and problems. The same thing happens to native mobile applications these days: when you want to update your software to make a change (whether it be from market demand or a bug or innovation) some percentage of your users will ignore the change and blissfully go on using their old versions of the software. Some apps have taken to battling this by disabling use of the older versions until they update, but this is a terrible user experience - user's don't want to have to worry about updating their version of your software, they just want it to work!

To sum up the issues with writing native apps:

	
  * Many different device platforms

	
  * Differentiations in the devices and OS versions within the same platform

	
  * Multiple languages to write software in, and different UI's across the different devices

	
  * Deploying updates can be difficult because users do not want to download and install new versions

	
  * One more issue specific to iOS - Apple has a **review** process, where they will approve your application or not, and if they don't like it you won't get to distribute your application to their customers




**Writing Web (HTML5) Apps**
In Mark Suster's strong piece, [App is Crap](http://www.bothsidesofthetable.com/2010/02/17/app-is-crap-why-apple-is-bad-for-your-health/), he argues that mobile applications will be the way of the future. If you think back to my example about bug-tracking software it's easy to see the parallel to mobile software. In 2010 (almost) nobody runs a native desktop version of bug-tracking software - they all run web-based tools like [bugzilla](http://www.bugzilla.org/). The ubiquity of browsers with standards has led to application development being about writing applications for the web standard, and anyone with a modern browser being able to access it. If a new hot operating system platform came out tomorrow (fat chance of that) as long as it had a modern browser written, that user would have access to all the same web applications users of windows and OS X would. 

A few years ago a friend and I were talking about what might be included in the next versions of the browser, and I said I thought that the introduction of vector graphics would be revolutionary, as all these background images and text effects created in photoshop would eventually be done in the browser. Fast forward a few years and HTML5 and CSS3 are finally bringing that promise to reality. HTML5 and CSS3 are next-generation variants of the underlying language powering the web - developers write their web-based software in using these technologies, and browsers interpret them (with others, like javascript) into the applications we know and love. This has also proved big for mobile devices, as features once available only for native apps are now available for web devices.

One of these features is the ability to detect touch and swipe gestures, specific to touch devices. This allows mobile web applications to respond to these events and not just think of the world as clicks. Mobile web frameworks such as [jqTouch](http://www.jqtouch.com/) and [Sencha Touch](http://www.sencha.com/products/touch/) allow mobile web developers to develop better software with less code, and the proliferation of larger devices will lead to more searching on the device (as opposed to just downloading apps), which will result in more opportunities for developers to market their web-based apps.

There are limits to what a web-based mobile application can do, however:



	
  * Mobile web applications cannot access some device specific features, like the camera, dialer, and contact list (note that the [user's location can be used in HTML5](http://diveintohtml5.org/geolocation.html))

	
  * Mobile web applications aren't quite as sensitive to user's actions as native apps are, and some actions are not accessible for mobile web apps

	
  * There is no major app store for mobile web applications



The last point, the app store, seemed like the most compelling reason for my co-founder and I to go with native apps over mobile web apps. We figured that when we built a iOS mobile app and put it in Apple's app store, people would download it, and we'd have instant distribution. After meeting with a few people familiar with this space, we discovered this is just not the case. Almost universally we heard that distribution is "difficult", you need to "get lucky", and that users "don't search, they download from the top 10 lists". We were most surprised to hear this reason, as it wiped out one of the biggest reasons to develop a native version of our app.

**Final Thoughts**
Ultimately there are pros and cons to building native and web-based mobile apps, at least in 2010. Coming from a web background, and subscribing to the "[lean-startup](http://en.wikipedia.org/wiki/Lean_Startup)" approach of iteration, I feel more comfortable with building a web application, looking at what my user's are telling me with their actions (measurable web data - in clicks and touches), and making changes based on that feedback. Time will tell if I'm right, but I am betting that mobile web apps - using HTML5 - are the future, and native mobile apps, like desktop apps before them, will be afterthoughts for all but a few in the future.


