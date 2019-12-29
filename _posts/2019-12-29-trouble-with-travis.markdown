---
layout: post
cover: 'assets/images/2019/12/Travis-silent-build-fail.png'
navigation: True
title: Trouble with Travis
date: '2019-12-29 14:54:40'
tags:
- blog
- jekyll
- travis
- english
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

Today I learnt that Travis don't like _tags_ with spaces in them. It took me over an hour to figure out, but there it is.

If you're using [Jekyll](https://jekyllrb.com/), [Github Pages](https://pages.github.com) and are building your blog using [Travis](https://travis-ci.org/) do not use tags with spaces in them. It doesn't help putting the tag into _apostrophe_ either.

It worked when I tried locally on my computer (Ubuntu in [WSL](https://docs.microsoft.com/en-us/windows/wsl/about) in Windows 10), but it fails silently when run using Travis.
