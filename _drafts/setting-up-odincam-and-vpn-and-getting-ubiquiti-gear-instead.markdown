---
layout: post
title: Setting up OdinCam (and VPN) and getting Ubiquiti gear instead
tags:
- ubnt
- ubiquiti
- network
- vpn
---

Our dog (Odin) has epilepsy. It's not fun. Back in November we thought his epilepsy was under (enough) control for us to leave him alone for a few hours again. We decided to get a webcam to keep an eye on him while we were out. I wanted a webcam with Power-over-ethernet (PoE) support. I started looking and found a few candidates. Then Black Friday came along and I found a nice D-Link webcam reduced with 40% and I bought it. When it arrived I realised that it was a wireless camera using micro USB for power. Setting it up was easy enough, but I don't trust D-links cloud (**FIND REFERENCE**) and wanted a different solution for accessing it from the internet. My idea was to install Surveillance Station and VPN-server on my 2015-model Synology NAS.

I got Surveillance Station installed and configured with the camera, and it seems to work just fine. I do like how easy it is to create a schedule for recording and the nice iOS app to view them. Then I started looking into the VPN server, but before I had time to install it Troy Hunt posted about his new [Ubiquiti home network](https://www.troyhunt.com/ubiquiti-all-the-things-how-i-finally-fixed-my-dodgy-wifi/). At this time Odin had gotten worse again, due to inflammatory bowel disease (IBD) and the OdinCam was put on hold. Since I now had time and to avoid having to set up VPN twice I decided to buy my own Ubiquiti gear before I continued. One of the reasons I decided to go for Ubiquiti gear is UniFi, their management system. It's really easy to use and very powerful, and it looks good.

Finding a supplier in Norway turned out to be challenging. I ended up ordering what I thought would be everything from Komplett.no, since they stocked everything. I bought:

- Security Gateway (USG)
- Switch 8 port 150W (US-8-150W)
- 802.11ac PRO Access Point (UAP‑AC‑PRO) x2
- Cloud Key

Thea idea was to put the USG, switch, Cloud Key and one AP in the TV bench and run ethernet to the office switch and install the second AP there, which I did. This worked fine, but I wasn't quite happy. The reason was the office switch. It's an cheap simple switch, and it meant that everything in the office appeared to be connected to the same port on the living room switch. This lack of information was nagging me, and I was very close to order another 8 port 150W switch. I'm very glad I didn't blow all that money on a second fully powered switch. While I was considering what to do, I realised Ubiquiti had released an 8 port UniFi switch powered through PoE with one PoE pass through port. This was exactly what I needed. Unfortunately Komplett.no didn't stock it, and they weren't interested in doing it either when I asked them. Looking around I did find a supplier (ProShop.no), but they had 2-3 months estimated delivery time. After a couple of weeks I decided it was better to order it now and wait for it to arrive than paying more than 2000NOK more for the 150W version. I ordered it on the third of January and didn't really expect it before late February. On the 10th I got a pleasant surprise as an email landed in my inbox and could tell me my switch was on its way.

It arrived this Thursday and I installed it immediately. To my horror it didn't work as expected. The switch got power from the living room switch, and I could adopt it with the UniFi Controller running on the Cloud Key, but the AP connected to the PoE pass through didn't boot. After trying a different cable, upgrading and restarting the switch, and a few other things I eventually looked in the user manual. It turns out the new switch had the PoE pass through turned off by default. By turning it on via the UniFi Controller the AP booted back up and my network was *complete*.

The UniFi Controller have a nice topology map view, you can see an example with (almost) all our devices here: **MARK COPYRIGHT CC...??**

![Ubiquiti UniFi topology map for our home network](/assets/images2/2017/01/Herskapshuset-UniFi-topology-map.png)

I still haven't configured VPN, mainly because the present version of the UniFi Controller (version 5.3.8) only supports PPTP and we only have iOS 10 devices, which does not support PPTP. Ubiquiti are working on support for configuring L2TP over IPSec through the GUI (it's already supported using CLI configuration), but it's still a little while away. More information on their [community site](https://community.ubnt.com/t5/UniFi-Routing-Switching/USG-Remote-User-VPN-with-iPhone/m-p/1791336#M31894). 

And other good [blog post](https://scotthelme.co.uk/my-ubiquiti-home-network/) about a Ubiquiti UniFi home setup is Scott Helme's. He has also written about [Setting up HTTPS on the UniFi CloudKey](https://scotthelme.co.uk/setting-up-https-on-the-unifi-cloudkey/) so you can get rid of the warning when connecting to it. I haven't done this yet, but it's something I'm planing to do in the not too distant future.




Find all local IPs:

> ping *.255
>
> arp -a
>
> netstat -r
