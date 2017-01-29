---
layout: post
title:  "\"Project not built in active configuration\" for new .Net Core Console Application under Visual Studio for Mac"
date:   2017-01-29 13:45:00 -0000
categories: .net core, console application, project not built in active configuration, visual studio mac
---
As is a depressingly regular occurrence, it seems that every time I have a flash of inspiration and decide to work on a new project outside of the relatively safe ecosystem that is C# .Net under Visual Studio 2017 on my Windows 10 machine I come a cropper, and today was no exception.

Buoyed by the enthusiasm of a new project, I fired up Visual Studio for Mac only to be prompted that it wants to update some components. Fine, I grabbed a coffee while it cracked on bringing my IDE up to date with the latest Stable. Once finished I created a new .Net Core Console project and was hoping to crack on, only to discover my first hurdle. 

![Project not build in active configuration tooltip on Project entry in Visual Studio Preview]({{ site.url }}/assets/ProjectNotBuiltInActiveConfigurationToolTip.png "Project not build in active configuration")

While apparently building with no errors, there was no active configuration to allow me to Run/Debug under.

![Greyed out debug menu in Visual Studio Preview]({{ site.url }}/assets/DebugMenuEmpty.png "Greyed out Debug options")

It appears that the update to Visual Studio now has a dependency on a version of the .Net Core SDK that isn't on my machine. A quick check of /usr/local/share/dotnet/sdk reveals that I only had version 1.0.0-preview2-02121. 

In my haste to update, I hadn't read the [release notes](https://developer.xamarin.com/releases/vs-mac/preview/vs-mac-preview1/) including this little tidbit:

> In order to run .NET Core projects, [.NET Core SDK 1.0 RC 4](https://dotnetcli.blob.core.windows.net/dotnet/Sdk/rel-1.0.0/dotnet-dev-osx-x64.latest.pkg) must be downloaded and installed

In this case it was my bad for not paying closer attention to the release notes, in particular when running preview or beta software. I do feel however that the whole .Net cross platform development story could be a lot more polished. As someone who occasionally revisits the idea of C# .Net/Mono development on MacOS I find each time I do, I have to spend a considerable amount of time getting just the basics working again. Why the VS updater couldn't have either flagged this new missing dependency to me or just installed it is beyond me.


