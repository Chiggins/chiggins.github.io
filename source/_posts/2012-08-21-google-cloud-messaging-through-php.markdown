---
layout: post
title: "Google Cloud Messaging through PHP"
date: 2012-08-21 16:15:01 -0500
comments: true
categories: php, gcm, android
---
A few weeks ago I ran into an article on how to use Google Cloud Messaging with the .NET Framework. That got me thinking, and I wanted to give it a shot in PHP, it couldn’t be too bad right? So, here’s just some simple code on crafting the POST request to send to a specified Android device. All you need to do is supply your own various IDs from Google and whatever Android device you want to send to (as long as it’s registered) and you’re all set. Take a look at my code:
<!--more-->
{% gist 9923471 %}
