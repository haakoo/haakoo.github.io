---
layout: post
cover: 'assets/images/2021/08/2021-08-01-Finished-PDF-with-pictures.jpg'
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

I needed to create a PDF with multiple pictures per page. The pictures had to be numbered and include a timestamp. All the photos were in Lightroom, which we use to manage our photos. Using a plugin, I added the necessary watermarks during export. Trying create a PDF with the 50 or so pictures in chronological order using Windows 10's _print photo_ didn't work very well. I needed a different solution.

Below, I'll go through the different steps I used to create the PDF.

## Export images from Adobe Lightroom

First, I used a plugin called [LR/Mogrify 2](https://www.photographers-toolbox.com/products/lrmogrify2.php) from [Photographer's Toolbox](https://www.photographers-toolbox.com/index.php) by Arctic Whiteness. This is a plugin that adds functionality to the export dialogue in Adobe Lightroom.

The settings I used to create the two watermarks were:

![Settings to add the picture date as watermark](assets\images\2021\08\2021-08-01-LR-Mogrify-plugin-settings01.png)

![Settings to add the picture number as watermark](assets\images\2021\08\2021-08-01-LR-Mogrify-plugin-settings02.png)

## Creating the PDF

To create the PDF I used [Pandoc](https://pandoc.org) to compile a very simple markdown file. The markdown file only contained image insertions as shown below:

```markdown
![](picture001.jpg){width=33%}\ 
![](picture002.jpg){width=33%}\ 
![](picture003.jpg){width=33%}\ 

![](picture004.jpg){width=33%}\ 
![](picture005.jpg){width=33%}\ 
![](picture006.jpg){width=33%}\ 

...
```

I then compiled the markdown file to a PDF using the following pandoc command:

```terminal
pandoc document.md -V geometry:margin=10mm -V papersize=a4 -f markdown -o document.pdf
```

I've created an example file ([2021-08-01-Finished-PDF-with-pictures.pdf](assets\files\2021\08\2021-08-01-Finished-PDF-with-pictures.pdf) (13 MB)) sporting our dog [Odin the Viking Toller](https://www.instagram.com/odinthevikingtoller).
