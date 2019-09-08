---
layout: post
title: Getting Ghost up and running on Mac OS X
date: '2015-07-18 21:51:50'
tags:
- english
- ghost-tag
- blog
- development
- node-js
- mac-os-x
---

I figured it would be nice to have Ghost up and running locally on my machine if I'm to mess around with themes. So today I installed [Node.js](https://nodejs.org/), cloned Ghost from [GitHub](https://github.com/TryGhost/Ghost) and got it all working.

I followed the instructions from https://github.com/TryGhost/Ghost#developer-install-from-git with a few tweaks. You need to run the `npm install` commands using sudo (they will fail and then tell you to rerun as root). I also downloaded and installed Node.js v0.10.40 from [install package](http://blog.nodejs.org/release/). Node.js v0.10.40 has several security fixes and is probably a better choice than v0.10.36 I saw recommended somewhere.

Surprisingly easy to get it all running when I figured out that `npm install` needs root permissions and `grunt`does not after a tip from [@acburdine in #ghost on Ghost Slack](https://ghost.slack.com/archives/ghost/p1437257215000010).

*Edit 2015-07-19:* It should be possible to run `npm install` without `sudo`, according to [@fabian over at Ghost Slack](https://ghost.slack.com/archives/ghost/p1437262059000023). I'll see if I can reproduce my troubles from yesterday and figure out what was wrong.
