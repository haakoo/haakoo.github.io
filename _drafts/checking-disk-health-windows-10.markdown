---
layout: post
title: Introduction to unmanned systems
tags:
- blog
- english
- windows 10
- ssd
- hard drive
---

## Checking disk health in Windows 10

Get smart status with the following command.

```powershell
 wmic diskdrive get caption,model,status,statusinfo,size
```

Example output:

```powershell
PS C:\Users\haako> wmic diskdrive get caption,model,status,statusinfo,size
Caption                           Model                             Size           Status  StatusInfo
Microsoft Virtual Disk            Microsoft Virtual Disk            8587192320     OK
Generic SM/xD-Picture USB Device  Generic SM/xD-Picture USB Device                 OK
Generic Compact Flash USB Device  Generic Compact Flash USB Device                 OK
Generic MS/MS-Pro/HG USB Device   Generic MS/MS-Pro/HG USB Device                  OK
Generic SDXC/MMC USB Device       Generic SDXC/MMC USB Device       63861073920    OK
WDC WD30EFRX-68EUZN0              WDC WD30EFRX-68EUZN0              3000590369280  OK
Samsung SSD 970 EVO Plus 1TB      Samsung SSD 970 EVO Plus 1TB      1000202273280  OK
```

More info here https://www.windowscentral.com/how-check-if-hard-drive-failing-smart-windows-10
