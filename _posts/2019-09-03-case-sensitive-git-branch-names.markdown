---
layout: post
cover: 'assets/images2/git-case-sensitive-branch-names.png'
navigation: True
title: case sensitive git branch names
date: '2019-09-03 07:17:31'
tags:
- english
- windows
- linux
- git
- gitlab
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

I've had some fun with `git` again... I was checking out a remote branch with `git` on the command line and couldn't pull down updates. Eventually I found out that the problem was case sensitivity in the branch name.

I used `git checkout branch-name` to get a local copy of the remote branch. When I tried to use `git pull` in that branch I got the following error message:

```
Your configuration specifies to merge with the ref 'refs/heads/branch-name' from the remote, but no such ref was fetched.
```

I tried to search for an fix, but couldn't find anything that worked. The most common explaination for this error message is that the remote branch is missing.

Eventually I remembered that I had used a capital letter in the branch name when creating it. The actuall branch name was something like `branch-Name`, notice the capital **_N_**. By having the correct capitalising of the branch name during checkout, `git pull` works.

This was checking out from Gitlab on a Linux server and to a Windows 10 machine.
