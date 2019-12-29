---
layout: post
cover: 'assets/images/2019/12/PhotoRec-08-finished-recovering-files.png'
navigation: True
title: Recover lost images from SDcard
date: '2019-12-29 14:29:43'
tags:
- Canon
- EOS
- 60D
- sdcard
- memorycard
- lost-photos
- recover-photos
- sandisk
- english
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

We had a scare when all the photos from 24th and 25th of December disappeard from our memory card. Lukily I managed to recover them using [PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec).

We have a well used Canon 60D and apparently a dying [SanDisk Extreme PRO 32GB](https://shop.westerndigital.com/products/memory-cards/sandisk-extreme-pro-uhs-ii-sd#SDSDXPK-032G-ANCIN) memory card. The card isn't new, and thinking back I'm not sure this is the first time it's behaved like this. When we were going to copy the pictures from the memorycard they disappeared. The pictures had been visible on the camera, but when we opened the card in Windows only images about a month old was visible. No photos from the last two days. Something had happend to the memorycard and it had lost part of the File Allocation Table (FAT), so the new image files where _"gone"_. I have no idea how this happened, but I no longer trust that memory card.

Hoping to recover the files I went looking for a solution online. I spent quite a while trying tools, like _SanDisk RescuePRO Deluxe_ and _Lexar Recovery Tool for Windows_. Lexar Recovery tool didn't find anything on the card, not sure if that's because it is a SanDisk card or not. _SanDisk RescuePro_ did find the missing photos, and gave me a preview of them. If I wanted to restore the photos, I had to buy the software for $60 USD, which felt a bit expensive.

After I knew the photos were on the card I decided to search for another solution that didn't cost $60. Eventually I came across this [question over at ask Ubuntu](https://askubuntu.com/questions/330568/how-to-restore-photos-on-sd-card). That led me to the PhotoRec homepage and to the [Step by step guide](https://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step).

## Solution

I downloaded [TestDisk Zip-archive](https://www.cgsecurity.org/wiki/TestDisk_Download) and extracted it to a temp folder. After that it's fairly straight forward, my choices in paranteses:

0. Activate write lock on your memory card and put it in your computer
1. Run 'photorec_win.exe' as an administrator
2. Select which media to recover from ('Generic SDXC')
3. Select which partition on the media ('EOS DIGITAL')
4. Select what filesystem the partition have ('FAT/NTFS/HFS+/ReiserFS/...')
5. Select what space to be analysed ('free' or 'whole')
6. Select where to store the recovered files ('C:\Temp\photorec')
7. Choose 'C' to confirm location
8. Wait
9. Quit 'photorec'

### Screenshots of the steps

#### Step 1

![Run PhotoRec as Administrator](/assets/images/2019/12/Run-PhotoRec-as-Administrator.png)

#### Step 2

![PhotoRec command line window - Select media](/assets/images/2019/12/PhotoRec-02-select-media.png)

#### Step 3 

![PhotoRec command line window - Select partition](/assets/images/2019/12/PhotoRec-03-select-partition.png)

#### Step 4

![PhotoRec command line window - Select filessytem](/assets/images/2019/12/PhotoRec-04-select-filesystem.png)

#### Step 5

![PhotoRec command line window - Select space to be analysed](/assets/images/2019/12/PhotoRec-05-select-space-to-be-analysed.png)

#### Step 6

![PhotoRec command line window - Select where to store recovered files](/assets/images/2019/12/PhotoRec-06-select-where-to-store-recovered-files.png)

#### Step 7

![PhotoRec command line window - Progress - Recovering files](/assets/images/2019/12/PhotoRec-07-recovering-files.png)

#### Step 8

![PhotoRec command line window - Progress - Finished](/assets/images/2019/12/PhotoRec-08-finished-recovering-files.png)

## Summary

I successfully recovered the missing photos from the memorycard using [PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec) and are going to replace the aging / faulty memory card.
