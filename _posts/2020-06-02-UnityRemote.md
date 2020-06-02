---
layout: post
title: UnityRemote
date: 2020-06-02 11:00:05 UTC+8
tags: [Unity,Remote]
category: [Software]
description: Unity,Android
---

Unity Remote是Unity公司提供的一个移动端同步调试工具，在Unity编辑器中以播放模式运行项目时，该应用程序将与Unity连接。 编辑器的可视输出被发送到设备的屏幕，实时输入被发送回Unity中正在运行的项目。这样可以节省项目调试的时间。

<!-- more -->

# 下载

Unity Remote之前就有，东躲西藏，以前在商城里，后面被移出商城了。现在在发布公告的页面可以下载。

![下载UnityRemote](/images/20200602-UnityRemote-01.jpg)

![下载UnityRemote](/images/20200602-UnityRemote-02.jpg)

官方说明地址：[https://docs.unity3d.com/Manual/UnityRemote5.html](https://docs.unity3d.com/Manual/UnityRemote5.html)

# 要求

- 安卓版的要求本地有Android SDK
- 移动设备开启调式模式
- 安装Unity Remote
- 用USB将电脑和移动设备连接
- 在Unity编辑器中设置

![Unity设置](/images/20200602-UnityRemote-03.jpg)

- 在移动端打开Unity Remote

![Unity设置](/images/20200602-UnityRemote-04.jpg)

# 效果

在编辑器点击运行以后，就能同时在移动设备和屏幕上看到效果。

![UnityRemote效果](/images/20200602-UnityRemote-08.jpg)

注意要把调式的分辨率设置到和移动设备一致，不然，移动设备上显示的内容会变形。

![UnityRemote效果](/images/20200602-UnityRemote-06.jpg)

# 连接问题

有时候会连接不上，编辑器在运行了移动端没反应。通常重启一下Unity编辑器就可以了。实在不行，可以到Android SDK目录下，用“adb devices”命令看下是否真连接上了。

![UnityRemote连接](/images/20200602-UnityRemote-07.jpg)

# 其他

官方说明，Unity Remote能够实时反馈的内容包括触控点击，加速度计，陀螺仪，摄像头视频流，罗盘，GPS等。但是我使用下来发现，触控点击，加速度计，陀螺仪没问题，摄像头视频流，罗盘，GPS没反馈。我用的是Unity Remote5+小米8SE+Unity2019.3，不确定是哪的问题。

总之，Unity Remote虽然不完美，但是还是能提供一些开发上的便利。