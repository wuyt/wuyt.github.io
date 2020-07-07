---
layout: post
title: Unity2018下Android SDK设置
date: 2019-04-08 14:28:05 UTC+8
tags: [Unity]
category: [blog]
description: Unity2018下Android SDK设置
---

Unity3D 2018.3版本以后，要求Android SDK版本需要在26.1.1以上。之前Android SDK是有图形界面的，26.1.1之后只提供了命令行的方式。

<!-- more -->

## Unity3D发布Android app时，用到的Android SDK组件说明

- Android SDK Tools（必须）
- Android SDK Platform-tools（必须）
- Android SDK Build-tools（使用最高版本即可，但不要使用预览版，即带rc的版本）
- SDK Platform（使用对应版本，即发布那个版本的app，必须有对应版本的SDK Platform）

## Unity3D 2018.3关于Android SDK 版本提示

Android SDK 25.2.5版本以前是有图形界面的，有个“SDK Manager.exe”文件，运行后有图形界面，如下图。可以在图形界面进行添加和删除。

![旧的图形界面](/images/2019-4-8-sdkmanager.jpg)

在Unity3D 2018.3版本以后，Build的时候会有以下提示。

![提示信息](/images/2019-4-8-prompt.jpg)

此时，点击【Use Highest Installed】按钮，可以正确编译。

## Android SDK 26.1.1的安装和使用

Android SDK 26.1.1的下载地址
https://developer.android.google.cn/studio

![下载](/images/2019-4-8-download.jpg)

解压以后，在目录中有个“sdkmanager.bat”文件。

![下载](/images/2019-4-8-bat.jpg)

用命令行的方式，进行操作即可。最常用的3个命令是

- sdkmanager --list（查看已经安装的内容）
- sdkmanager packages（安装）
- sdkmanager --uninstall packages（卸载）

在使用“list”参数后，还能看到可以安装的内容的列表。

![列表](/images/2019-4-8-list.jpg)

## 使用中的其他提示

Target Android SDK not installed

![缺少对应版本SDK](/images/2019-4-8-target-not-installed.jpg)

这个提示是缺少对应版本的SDK Platform，重新添加一下即可。

Gradle build failed

![Gradle build failed](/images/2019-4-8-Gradle-build-failed.jpg)

![Gradle build failed](/images/2019-4-8-Information.jpg)

这个，有可能是使用了预览版的Android SDK Build-tools造成的，删除后从新安装一个即可。