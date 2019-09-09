---
layout: post
title: VS Code Unity使用设置
date: 2019-09-09 14:10:05 UTC+8
tags: [VS Code,  Unity3D]
category: [Software]
description: VS Code Unity使用设置
---

Unity3D在2017版以后，默认是用Visual Studio作为脚本编辑器，但是VS实在太大了，还是用VS Code方便，小巧灵活。

<!-- more -->

## 下载

VS Code下载地址：

https://code.visualstudio.com/

当前版本：1.38.0

## 关联Unity

Unity下打开Preferences窗口，在【External Tools】中修改【External Script Editor】选项，找到Code.exe文件，即可设置。

Code.exe文件默认路径是

C:\users\{username}\AppData\Local\Programs\Microsoft VS Code\Code.exe

![Unity设置](/images/2019-9-9-VSCode-Unity-Settings.jpg)

## 插件安装

安装的插件如下

![VSCode插件](/images/2019-9-9-VSCode-Unity-Plugins.jpg)

其中，c#插件需要安装.net core。

Debuger for Unity、Unity Code Snippets、Unity Snippets和Unity Tools插件是开发Unity用到的。

## VS Code其他设置

![文件隐藏](/images/2019-9-9-VSCode-Unity-jsion.jpg)

在VS Code中隐藏其他文件文件，打开settings.json配置文件添加

 >  // Configure glob patterns for excluding files and folders.
    "files.exclude": {
        "**/.git": true,
        "**/.DS_Store": true,
        "**/*.meta": true,
        "**/*.*.meta": true,
        "**/*.unity": true,
        "**/*.unityproj": true,
        "**/*.mat": true,
        "**/*.fbx": true,
        "**/*.FBX": true,
        "**/*.tga": true,
        "**/*.cubemap": true,
        "**/*.prefab": true,
        "**/Library": true,
        "**/ProjectSettings": true,
        "**/Temp": true
    }
