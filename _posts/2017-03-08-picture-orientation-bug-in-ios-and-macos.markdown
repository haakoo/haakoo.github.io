---
layout: post
title: Picture orientation bug in iOS and macOS
date: '2017-03-08 20:51:40'
tags:
- english
- mac-os-x
- windows
- macos
- exif
- photos
- pictures
---

A friend showed me a problem she had with one of the pictures on her webpage, http://lenefredriksen.com/. In Safari, Chrome and Vivaldi on macOS Sierra and Chrome and Vivaldi on Windows 7, all the pictures had the correct orientation. As in the following screen capture of Safari on macOS below.

![Screen capture of lenefredriksen.com in Safari on macOS Sierra](/content/images/2017/03/Safari.png)

In Safari on iOS, one of the pictures on the front page was rotated 90 degrees clockwise, as seen in the screen capture from my iPad below. I checked the source in both macOS and on my phone, but it was the same on both platforms and it looked fine. 

![Screen capture of lenefredriksen.com in Safari on iOS](/content/images/2017/03/iPad.PNG)

My next step was to download the picture that was rotated and one of the other pictures to compare them. When opening both pictures in QuickLook on my Mac, one was rotated and one was not. This sort of made sense, since that's how they appeared on the webpage in iOS.

![Screen capture of the rotated image in QuickLook on macOS Sierra](/content/images/2017/03/MacOS-Sierra-QuickLook.png)

What didn't make sense was why both were the right way up on almost all platforms and browsers. Looking at the EXIF data I found that the orientation was set to `1 (Normal)` for the one that was right way up, and `6 (Rotated 90 degrees counter clockwise)` for the picture that looked rotated.

![Showing the EXIF information for the two images in Previews Inspector](/content/images/2017/03/Orientations.png)

**It turns out that the problem is that QuickLook and Preview on macOS, and Safari on iOS don't rotate the picture according to the EXIF data.**

The solution was simple: open the rotated picture in Preview and rotate it so it's correct, and then save it. I assume the same can be done using Windows Photo Viewer if you're using Windows. If it looks the right way up when you open it, try rotating back and forth and save the changes.

A last hint at the end, you'll find the Inspector for Preview under `Tool`and `Show Inspector`.

![Screen capture that show where the Inspector can be found in the Preview menus](/content/images/2017/03/Preview-Show-Inspector.png)
