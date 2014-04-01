---
layout: post
title: "BSides Chicago 2013 CTF Challenge #31 Write Up"
date: 2013-04-30 13:45:44 -0500
comments: true
categories: ctf, bsides_chicago, .net, reversing
---
The BSides Chicago 2013 CTF was a fun one and quite the learning experience, so here’s my first ever write up and it’s going to be on challenge #31, easy reverse engineering on a .NET console application.

{% img center /images/bsides_2013_31/1.jpg %}

<!--more-->

Here is the challenge description:

{% blockquote %}
As a new agent, you may have some fears about being treated less than what you are worth. Well don’t you worry your little head one little bit tiger. You’ll be treated with the same level of respect as every other agent here. You are your own person. Ready to take on the challenges here. We consider you one of our top agents!

We have recovered an executable from the rogue agent’s computer. Please analyze the file and crack the key. We picked you because you are the brightest and the best, but before you start can you get me some coffee?
{% endblockquote %}

The application seems to be pretty straight forward. Just a simple login form that when properly authenticated, would show the key that you need in order to complete the challenge.

{% img center /images/bsides_2013_31/2.jpg %}

Opening the executable in IDA showed a ton of .NET assembly references. Since that was the case, I decided to open the exe up in Reflector instead for better working with .NET. I disassembled the file and began to look at the main() function.

{% img center /images/bsides_2013_31/3.jpg 740 %}

Looking at the code, you can see that you can totally skip past the while loop to bypass authentication. Then at the top you can see where a Base64 encoded string converted into a byte array is supplied. That is referenced after the login code, where it’s SHA1 hash is computed, then turned into a Base16 string with the custom ToBase16 method:

{% img center /images/bsides_2013_31/4.jpg 740 %}

With all of this information, I decided to spin up Visual Studio quick, copy paste over the necessary code that I needed and generate the key myself.

{% img center /images/bsides_2013_31/5.jpg 740 %}

{% img center /images/bsides_2013_31/6.jpg %}

Oh hello there key. End up doing some copy/pasta into the CTF framework, submit it, and receive points! I rarely do any reverse engineering, so this was a very cool learning experience for me and I thought that it would be cool to share with others.
