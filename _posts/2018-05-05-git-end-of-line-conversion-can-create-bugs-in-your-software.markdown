---
layout: post
title: Git end-of-line conversion can create bugs in your software
date: '2018-05-05 06:25:10'
tags:
- git
- english
- development
- bug
- fix
- c
- net
---

We were experiencing a strange bug with a C# library with an embedded binary file. It worked on the developers machine, but not after it was released after being built on a build server.

It turns out that the developer had _git checkout end-of-line_ settings that preserved the `LF` character, while the build server converted from `LF` to `CR LF` upon checkout. This corrupted the binary file that was embedded into the library as an _embedded resource_. Git didn't recognise the file type and interpreted it as a (partial) text file.

## The fix
I think the preferred way to avoid this is to include a `.gitattributes` file in the root-folder of your repo. In the `.gitattributes` file you specify how [git should handle different file types](https://git-scm.com/docs/gitattributes). For us the solution was to add the following:

```
*.pgm binary
```

I first found the solution for this in an answer on Stack Overflow, [How to change line-ending settings](https://stackoverflow.com/a/40821931/930546).

## Alternative
It's also possible to avoid this by changing the git setting `core.autocrlf` to either `input` or `false`, but this will change the behaviour for all files.