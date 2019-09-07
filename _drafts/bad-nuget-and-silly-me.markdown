---
layout: post
title: Bad NuGet and silly me?
---

https://twitter.com/haakoo/status/1083822337085112323

The problem? Not sure how the project ended up with reference to System.Windows.Interactivity wrapped in a nuget-package that wasn't referenced from the project. Probably from back when I upgraded from .NET 4 and MVC 3.


1. System.Windows.Interactivity had hint path to NuGet package
2. Didn't use that NuGet-package

Gaaaaaah!

```


<Reference Include="Caliburn.Micro, Culture=neutral">
      <HintPath>..\3rdLibs\Caliburn.Micro.dll</HintPath>
</Reference>

<Reference Include="System.Windows.Interactivity, ... >
<HintPath>..\packages\Caliburn.Micro.1.0.0\lib\Net40\System.Windows.Interactivity.dll</HintPath></Reference>

```