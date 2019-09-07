---
layout: post
title: Convert from Hg to Git on Windows
---


Konvertere fra hg til git
https://git-scm.com/book/en/v2/Git-and-Other-Systems-Migrating-to-Git



[grep --text](https://bbs.archlinux.org/viewtopic.php?id=32328)


[LC_ALL='C'](https://stackoverflow.com/questions/17210296/removing-duplicate-lines-from-text-file)


> hg log | grep --text user: | LC_ALL='C' sort | LC_ALL='C' uniq | LC_ALL='C' sed 's/user: *//' > ../authors





1. Installerte python
2. Pip install mercurial
3. Krever Visual C++ 9.0 for python




Encoding of authors and filenames:
> -encoding cp1252 --fe cp1252

https://docs.python.org/2/library/codecs.html#standard-encodings