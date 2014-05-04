---
author: Simon
comments: true
date: 2010-06-16 18:25:41+00:00
excerpt: I had a bit of an issue getting <a href="http://sphinxsearch.com/">Sphinx
  Search</a> running with MediaWiki in OSX as I found creating a plist to be a harder
  problem than I anticipated. I followed the standard <a href="http://www.mediawiki.org/wiki/Extension:SphinxSearch#Installation_Instructions">Mediawiki</a>
  installation instructions until I got to the point of setting up the daemon.
layout: post
slug: getting-sphinx-search-running-with-mediawiki-on-osx
title: Getting Sphinx Search Running with MediaWiki on OSX
wordpress_id: 233
categories:
- Mediawiki
tags:
- dev
- mediawiki
---

I had a bit of an issue getting [Sphinx Search](http://sphinxsearch.com/) running with MediaWiki in OSX as I found creating a plist to be a harder problem than I anticipated. I followed the standard [Mediawiki](http://www.mediawiki.org/wiki/Extension:SphinxSearch#Installation_Instructions) installation instructions until I got to the point of setting up the daemon.

In OS X it turns out the way to get a daemon to run is to run using [launchd](http://developer.apple.com/mac/library/documentation/MacOSX/Conceptual/BPSystemStartup/Articles/Daemons.html). The process to get one of these to run is to create an XML file in `/Library/LaunchDaemons` (there OS X has it's own plist files in `/Library/LaunchDaemons`) and run [`launchctl`](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=launchctl) to start the daemon.

I created my own daemon file for Sphinx, sphinx, in /Library/LaunchDaemons:

[xml]
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>Label</key>
        <string>org.search.sphinx</string>
        <key>UserName</key>
        <string>simon</string>
        <key>ProgramArguments</key>
        <array>
                <string>/usr/local/bin/searchd</string>
                <string>--config</string>
                <string>/Users/simon/source/mediawiki/wikinutrition/private/sphinx.conf</string>
        </array>
        <key>StandardOutPath</key>
        <string>/var/log/sphinx/sphinx-startup.log</string>
        <key>KeepAlive</key>
        <true/>
        <key>debug</key>
        <true/>
        <key>RunAtLoad</key>
        <true/>
</dict>
</plist>
[/xml]
You can see I am running the daemon as myself using the **UserName** key.

Unfortunately when I went to start this using `launchctl load -w /Library/LaunchDaemons/sphinx` nothing appeared to happen. No error message, no nothing. When I turned the debug setting on (by adding <key&gtdebug</key><true/>), however, I noticed in `/var/log/system.log` a number of these messages:

`
Jun 15 17:13:26 simon-mosk-aoyamas-computer-6 com.apple.launchd[1] (org.search.sphinx): Throttling respawn: Will start in 10 seconds
`

Googling this led to this [discovery from Apple](http://developer.apple.com/macosx/launchd.html):



> 
Jobs run from launchd should not duplicate launchd functionality; for instance, they should not use chroot(2). Furthermore, they should not do the things normally required of daemon processes, such as detaching from the terminal they are initially attached to. The only things that are strictly prohibited, however, are fork()/exit() combinations (including indirect methods, such as the daemon(3) library call). A server which attempts to run itself as a daemon in this way will seem to have finished running, potentially leading to launchd respawning it, or disabling the service. As launchd does not get stalled waiting for a child that hasn't yet exited, it's not necessary to try to prevent it.




Bingo - here is the problem - Sphinx's searchd starts and forks as it's a traditional daemon. Thankfully it has a `--console` option which does not fork, so adding  `--console` to the plist file (inside the <ProgramArguments> array) had me up and running!

The final file:
[xml]
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>Label</key>
        <string>org.search.sphinx</string>
        <key>UserName</key>
        <string>simon</string>
        <key>ProgramArguments</key>
        <array>
                <string>/usr/local/bin/searchd</string>
                <string>--config</string>
                <string>/Users/simon/source/mediawiki/wikinutrition/private/sphinx.conf</string>
                <string>--console</string>
        </array>
        <key>StandardOutPath</key>
        <string>/var/log/sphinx/sphinx-startup.log</string>
        <key>KeepAlive</key>
        <true/>
        <key>debug</key>
        <true/>
        <key>RunAtLoad</key>
        <true/>
</dict>
</plist>
[/xml]

