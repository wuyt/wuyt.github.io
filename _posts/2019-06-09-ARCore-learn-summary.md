---
layout: post
title: ARCore 学习小结
date: 2019-06-09 19:10:05 UTC+8
tags: [AR, ARCore, Unity3D]
category: [Software]
description: ARCore 学习小结
---

在苹果推出了ARKit之后，Google也推出了对应的SDK，即ARCore。

<!-- more -->

## 基本内容

官网地址：

https://developers.google.cn/ar/

https://developers.google.com/ar/

SDK地址：

https://github.com/google-ar/arcore-unity-sdk/releases

当前版本：1.9.0

## 主要功能

运动跟踪：让手机可以理解和跟踪它相对于现实世界的位置。

环境理解：让手机可以检测各类表面（例如地面、咖啡桌或墙壁等水平、垂直和倾斜表面）的大小和位置。

光估测：让手机可以估测环境当前的光照条件。

增强图像：摄像头视野中检测到图像时，ARCore 会告诉您这些图像在 AR 会话中的物理位置。

面部识别：摄像头视野中检测到人脸时，ARCore 会告诉您人脸在 AR 会话中的物理位置及相关信息。

## 使用要求

ARCore对使用设备有一定要求，在中国支持的设备主要是华为小米和三星的部分手机，具体请查看官网列表

https://developers.google.cn/ar/discover/supported-devices

## 基本结构

![基本结构](/images/2019-6-9-arcore-structure.jpg)

ARCore最基本的是“ARCore Device”游戏对象，官方提供了预制件。ARCore的基本设置是在一个默认名为“ARCoreSessionConfig”的配置文件中，如果需要进行图片识别的时候，还需要在配置文件中添加识别图片的数据文件。

官方提供了一个光照评估的预制件，叫“Environmental Light”，可以根据光照情况对场景中模型的明暗做出调节。

此外，在官方示例中，显示识别点点云的预制件“PointCloud”和检测平面并显示的脚本“Detected Plane Generator”在多数情况下可以直接拿来使用。

## ARCore应用

ARCore的应用运行时会检查设备是否安装了“AR Core”这个应用，如果没安装会自动提示安装。“AR Core”这个应用在Google、小米、华为和三星手机预置的应用商店中能找到并安装。

![预装应用](/images/2019-6-9-arcore-app.jpg)

## ARCore Instant Preview

官方提供了一个开发辅助工具，在Unity的编辑界面运行的时候会提示安装。可以不用将开发的应用发布到手机就能看到运行后的效果。不过，有部分功能不支持这样的方式预览。

![instant-preview](/images/2019-6-9-arcore-instant-preview.jpg)

![运行效果](/images/2019-6-9-arcore-instant-preview-show.jpg)

具体代码请参照官方的Demo，感觉使用起来不是很方便。

