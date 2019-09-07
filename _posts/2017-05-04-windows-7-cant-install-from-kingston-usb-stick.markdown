---
layout: post
title: Windows 7 can't install from Kingston USB stick
date: '2017-05-04 19:41:26'
tags:
- english
- windows
- error
- install
---

I recently discovered that it's impossible to install Windows 7 from a Kingston USB stick. It turns out this is a known problem with [Kingston](https://blogs.technet.microsoft.com/asiasupp/2012/03/06/error-we-couldnt-create-a-new-partition-or-locate-an-existing-one-for-more-information-see-the-setup-log-files-when-you-try-to-install-windows-8-cp/) [DataTravel](https://superuser.com/a/789435/117037) sticks. I had this problem while installing Windows 7 Pro on an old Panasonic Toughbook CF-31.

It's not obvious that you can't install from these USB sticks, since you can boot into the Windows 7 installer. Everything works up until you're partitioning your harddrive. There, you'll get an error message saying:

> Setup was unable to create a new system partition or locate an existing system partition. For more information, see the Setup log files.

![Screen shot showing the error message while installing Windows 7 from a Kingston DataTraveler USB stick.](/content/images/2017/05/Windows-7-Install-error---Setup-was-unable-to-create-a-new-system-partition-or-locate-an-existing-system-partition.-For-more-information--see-the-Setup-log-files.-1.jpg)

## Solution?
Use a different USB stick. I had a SanDisk stick that worked as expected.