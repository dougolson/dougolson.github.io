---
layout: post
title: Messing around with Pure Data
date: 2015-11-04 07:55 
description: Pure Data 
comments: True
---

First step - get [JackOSX](http://jackosx.com/) - an audio server for mac

Jack OSX is an OS X implementation of Jack, and it installs everything necessary to take full advantage of Jack on OS X.  This includes: 

	•  The Jack server :  the infrastructure you need in place to use Jack.

	• The JackRouter (JAR) * : JAR is a CoreAudio “user space” driver that allows any OS X CoreAudio application to become a Jack client.

	• The Jack audio plugins * : Both AU and VST “Jack-aware” audio plugins are provided, which can further expand the limitless audio routing possibilities when using Jack. 

	• The JackPilot application * : JackPilot offers an easy to use GUI interface that allows you to control the Jack server, and manage the audio connections between applications and/or plugins.

If you want to see [a very long list of applications that can work with Jack](http://jackaudio.org/applications/)