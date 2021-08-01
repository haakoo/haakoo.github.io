---
layout: post
# cover: 'assets/images/tents-in-the-night.jpg'
navigation: True
title: Creating a pdf with multiple pictures
date: '2021-08-01 17:45:00'
tags:
- english
- adobe lightroom
- markdown
- pandoc
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

I needed to create a pdf with multiple pictures as documentation. I needed the pictures to be numbered, and with a timestamp in them. Windows weren't very helpfull when trying to print the pictures in order from top left to right, so I needed a different solution.

## Export images from Adobe Lightroom

Used a plugin called [LR/Mogrify](https://www.photographers-toolbox.com/products/lrmogrify2.php) 2 from [Photographer's Toolbox](https://www.photographers-toolbox.com/index.php) by Arctic Whiteness.

## Creating the pdf

Created a very simple markdown document.

```markdown
![](picutre001.jpg){width=33%}\ 
![](picutre002.jpg){width=33%}\ 
![](picutre003.jpg){width=33%}\ 

![](picutre004.jpg){width=33%}\ 
![](picutre005.jpg){width=33%}\ 
![](picutre006.jpg){width=33%}\ 

...

```

And compiled it to a pdf using Pandoc.

```terminal
pandoc document.md -V geometry:margin=10mm -V papersize=a4 -f markdown -o document.pdf
```
