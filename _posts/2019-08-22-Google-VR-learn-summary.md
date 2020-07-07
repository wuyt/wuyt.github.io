---
layout: post
title: Google VR 学习小结
date: 2019-08-22 14:10:05 UTC+8
tags: [Google VR,  Unity]
category: [blog]
description: Google VR 学习小结
---

Google VR是Google公司的一款VR SDK，主要针对Google的Cardboard和Daydream设备。

<!-- more -->

## 基本内容

市面上很多低端的VR眼镜本质上都是Cardboard的加强款，将纸盒子变成了塑料盒子，使佩戴使用更舒服，并没有更多的技术上的提升，使用方法也是需要插入智能手机。所以，在面对低端的VR开发的时候，Google VR仍然是一款不错的VR SDK。

官网地址：

https://developers.google.cn/vr/

https://developers.google.com/vr/

SDK地址：

https://github.com/googlevr/gvr-unity-sdk/releases

当前版本：1.200.1

## 基本结构

![基本结构](/images/2019-8-22-gvr-structure.jpg)

在Google VR的场景中，只需要有“Main Camera”，启动以后，Google VR会自动将其变成横屏的VR模式。

- Player游戏对象是个空的游戏对象，目的主要是把视角提高到普通人的高度。

- Main Camera游戏对象需要在其下添加“GvrPointerPhysicsRaycaster”脚本。如果没有添加该脚本，则无法对Unity GUI之外的游戏对象进行注视并进行点击互动。

- GvrReticlePointer预制件的作用是生成注视的效果。

- GvrEventSystem预制件的作用是将使用者的注视和离开的效果转换成“Point Enter”和“Point Exit”事件，方便使用。

- 可注视对象，Google VR场景中游戏对象需要拥有“Collider”组件和“Event Trigger”组件才能响应注视事件。

- Unity GUI在Google VR中，Unity的GUI中的Button（按钮）、Toggle（选择框）、Slider（滑块）、Scrollbar（滚动条）、Dropdown（下拉列表）不需要处理即可响应点击事件，但是如果需要响应注视事件，还是需要添加“Event Trigger”组件。

- GvrEditorEmulator预制件的作用用在Unity编辑器中模拟VR效果。

- GvrInstantPreviewMain预制件的作用是让开发者可以利用“Instant Preview”应用进行连机调试。


