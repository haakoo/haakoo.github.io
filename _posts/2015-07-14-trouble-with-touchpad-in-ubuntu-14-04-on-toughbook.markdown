---
layout: post
cover: 'assets/images/tents-in-the-night.jpg'
navigation: True
title: Trouble with touchpad in Ubuntu 14.04 on Toughbook CF-31
date: '2015-07-14 07:20:59'
tags:
- english
- ubuntu
- toughbook
- touchpad
- fix
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

After I installed Ubuntu 14.04 LTS on a Toughbook CF-31 the touchpad wasn't working. The touch screen was working, and I could connect a USB mouse and use that. I tried to find a solution to the problem and searched and tried several things before I found the answer.

The solution is fairly simple, you need to edit `/etc/default/grub`[^1] (`sudo nano /etc/default/grub` - `Ctrl + X` to exit) and add `i8042.nomux i8042.noloop`[^2] to the line `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`. The resulting line should look like:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.noloop"
```

Then you need to update grub by running `sudo update-grub`.[^1]

The important next step is to **power cycle** your machine. A normal **reboot will not work** (not sure why). This caused me an hour's worth of grief yesterday, before I finally gave up and turned off the computer. When I started it this morning the touchpad worked.

## Other diagnostics

There is something you can do to figure out if you have the same problem that I did. You should check if the problem relates to the Linux kernel or driver. Run the command:[^3]

```
cat /proc/bus/input/devices
```

and if you can't see an entry with "Touchpad" the kernel hasn't found the hardware, and my fix might work. If you do see an entry with "Touchpad" then the problem is probably related to the driver, and this fix will not work.

### Footnotes
[^1]: http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/
[^2]: http://ubuntuforums.org/showthread.php?t=844968&p=5290024#post5290024
[^3]: http://askubuntu.com/questions/483229/dell-5537-touchpad-not-working-ubuntu-14-04
