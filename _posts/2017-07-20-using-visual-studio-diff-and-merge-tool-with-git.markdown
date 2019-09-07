---
layout: post
title: Using Visual Studio diff and merge tool with Git
date: '2017-07-20 10:00:00'
tags:
- english
- microsoft
- git
- sourcetreeapp
- diff
- merge
- vs2017
- visual-studio
---

On Windows I prefer to use Visual Studio's diff and merge tools. And since I use git I decided to change the default diff and merge tools to Visual Studio 2017 (VS2017).

## SourceTree App
I first changed the diff and merge tools in SourceTree App, just to test the settings. I found a nice blog post [Using Visual Studio as diff/merge tool in Git and SourceTree](http://blog.dudak.me/2016/using-visual-studio-as-diffmerge-tool-in-sourcetree/) by Michał Dudak explaining how to do this for VS 2015. Since Visual Studio 2017 have a different folder structure I had to look for `vsdiffmerge.exe` and with the help of the [comments for a Gist](https://gist.github.com/DamianReeves/35adf89992f8d871afe6#gistcomment-2024718) I found the correct location.

In the _Diff Options_ you choose to use _Custom tools_ and use the following settings:

**Command:** (same for both diff and merge)
```bash
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\TeamFoundation\Team Explorer\vsDiffMerge.exe
```

**Diff arguments:**
```bash
"$LOCAL" "$REMOTE" "Source" "Target" //t
```

**Merge arguments:**
```bash
"$LOCAL" "$REMOTE" "$BASE" "$MERGED" //m
```


## Git defaults using Git Bash

To change the git defaults using `Git Bash` you can do the following:

```bash
git config --global difftool.visualstudio.cmd "'C:/Program Files (x86)/Microsoft Visual Studio/2017/Enterprise/Common7/IDE/CommonExtensions/Microsoft/TeamFoundation/Team Explorer/vsdiffmerge.exe' \$LOCAL \$REMOTE Source Target //ignorespace //t"

git config --global mergetool.visualstudio.cmd "'C:/Program Files (x86)/Microsoft Visual Studio/2017/Enterprise/Common7/IDE/CommonExtensions/Microsoft/TeamFoundation/Team Explorer/vsdiffmerge.exe' \$LOCAL \$REMOTE \$BASE \$MERGED //ignorespace //m"
git config --global mergetool.visualstudio.trustExitCode true

git config --global diff.tool visualstudio
git config --global merge.tool visualstudio
```


## Git defaults using cmd.exe

To change the git defaults using `cmd.exe` you can do the following:

```shell
git config --global difftool.visualstudio.cmd "'C:/Program Files (x86)/Microsoft Visual Studio/2017/Enterprise/Common7/IDE/CommonExtensions/Microsoft/TeamFoundation/Team Explorer/vsdiffmerge.exe' $LOCAL $REMOTE Source Target //ignorespace //t"

git config --global mergetool.visualstudio.cmd "'C:/Program Files (x86)/Microsoft Visual Studio/2017/Enterprise/Common7/IDE/CommonExtensions/Microsoft/TeamFoundation/Team Explorer/vsdiffmerge.exe' $LOCAL $REMOTE $BASE $MERGED //ignorespace //m"
git config --global mergetool.visualstudio.trustExitCode true

git config --global diff.tool visualstudio
git config --global merge.tool visualstudio
```
