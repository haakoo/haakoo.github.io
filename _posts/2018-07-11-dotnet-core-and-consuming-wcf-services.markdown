---
layout: post
cover: 'assets/images/2018/07/DotNetCore_AddConnectedServiceContextMenu.png'
navigation: True
title: ".Net Core and consuming WCF services"
date: '2018-07-11 14:01:21'
tags:
- dotnet-core
- visual-studio
- wcf
- connected-service
- dotnet
- core
- english
- net
subclass: 'post' #important(!)
author: haakoo
categories: haakoo
---

I got stuck trying to figure out where the Visual Studio plugin _Visual Studio WCF Connected Service_ had gone today. It turns out it's no longer a plugin, but part of Visual Studio since version [15.5](https://docs.microsoft.com/en-us/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).

I'm converting an old .Net 4.0 project to .Net Core, and it is consuming a WCF-service. Everywhere i looked I found references to a Visual Studio plugin called _Visual Studio WCF Connected Service_, but it wasn't on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) anymore. After wasting about 30 minutes trying to figure out where to get the plugin I just tried to right click my .Net Core project, and lo and behold there I found _Add Connected Service_ and I could add my WCF-reference.

If only Microsoft could have left the plugin on the Marketplace and told us it was now part of Visual Studio...
