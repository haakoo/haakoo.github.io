---
layout: post
cover: 'assets/images/tents-in-the-night.png'
navigation: True
title: Renameing files by time created
date: '2019-01-?? 14:54:40'
tags:
- sdcard
- memorycard
- lost-photos
- recover-photos
- english
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---


https://stackoverflow.com/questions/3211595/renaming-files-in-a-folder-to-sequential-numbers

https://stackoverflow.com/questions/1404938/list-files-by-last-edited-date

https://superuser.com/questions/31464/looping-through-ls-results-in-bash-shell-script

https://www.cyberciti.biz/faq/ls-command-sort-the-output-by-last-modified-time-date/



```bash
ls -tr *.cr2 > filelist.txt # Create a file with a list of all the files sorted by time created
a=1 # We'll start the numbering of the files from 1
for i in $(cat filelist.txt); do new=$(printf "IMG_%04d.cr2" "$a"); mv -i -- "$i" "$new"; let a=a+1; done # Loop through all the files in the filelist and rename them to "IMG_0001.cr2", "IMG_0002.cr2" and so on
```
