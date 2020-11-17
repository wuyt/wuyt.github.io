---
layout: post
title: Unity常用插件:In-game Debug Console
date: 2020-11-17 11:00:05 UTC+8
tags: [Unity,Plugins,Debug,Console]
category: [Software]
description: Unity,Plugins
---

In-game Debug Console插件可以在打包发布以后，程序运行时方便的看到控制台信息，在一些特定程序开发的调试过程中非常有帮助。例如在开发一些AR程序的时候，如果官方没有提供支持，则只能将程序发布到移动设备后才能调试，这个时候，能在移动设备看到控制台信息对于开发会方便很多。

<!-- more -->

## 插件导入

在Unity商城搜索“debug”就可以找到这款插件，类似的还有其他一些插件。这个插件体积小，更新也比较即时。

![In-game Debug Console](/images/20201117-InGameDebugConsole-01.jpg)

导入的内容在【Plugins/IngameDebugConsole】目录下。

## 插件使用

将【Plugins/IngameDebugConsole】目录下的【IngameDebugConsole】预制件添加到场景中即可，这是会在平米右边的中间出现一个小的提示图标。

![In-game Debug Console](/images/20201117-InGameDebugConsole-02.jpg)

运行以后，图标会提示调试信息的数量，如果有错误，则图标会变成红色。

![In-game Debug Console](/images/20201117-InGameDebugConsole-03.jpg)

点击图标以后，会在屏幕上方显示调试信息的详细内容。

![In-game Debug Console](/images/20201117-InGameDebugConsole-04.jpg)