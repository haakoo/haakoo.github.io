---
layout: post
title: Batch add prefix to filenames windows 7
date: '2012-08-10 14:09:07'
tags:
- command-line
- windows
- english
---


I had a bit of a challenge wading through heaps of blogs and pages trying to find the easiest way to batch add a prefix to filenames. I wanted to add a prefix to all files in a folder, preferably using a vanilla windows command line prompt. The rename (ren) command was a good candidate, but I had some trouble with wild cards. To get it right I had to loop through the files.

The command I ended up using was:

```
for %f in (*.*) do rename "%f" "prefix-%f"
```

This will add ```prefix-``` to all files in that folder.
