---
layout: post
cover: 'assets/images2/tents-in-the-night.jpg'
navigation: True
title: Resetting corrupt "always available offline" database
date: '2015-12-03 13:01:05'
tags:
- english
- microsoft
- windows
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

For my work computer I keep a Outlook Data File (.pst), as a place to backup email. I keep the pst-file on my network share, which ensure that it's backed up. Recently I've experienced trouble with this solution when I've disconnected from the network while Outlook is running. I end up with a corrupt Offline Files Database which fail when syncing the pst-file. I can access the file while I'm not connected to a network, but as soon as I connect the file size appear to be 0 kB.

The only solution I've found to this problem is to reset the Offline Files Database, via [Delete Offline Files Cache Windows 7](http://www.technlg.net/windows/delete-offline-files-cache-windows-7/) and [this from Microsoft](https://support.microsoft.com/en-us/kb/942974).

You can do this by setting a flag in the registry.

1. Open regedit
2. Go to HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\services\CSC\Parameters
3. Create a new REG_DWORD named FormatDatabase with a value of 1
4. Restart computer
5. Add folders to the Offline Files Database

It's important to remember to re-add the folders to make them available offline again after the restart.


To reapply group policies use the command ([from this page](https://support.microsoft.com/en-us/kb/942974)):

> gpupdate /force
