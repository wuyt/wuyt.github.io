---
layout: post
title: Unity2019常用功能:Canvas画布
date: 2021-1-5 11:00:05 UTC+8
tags: [Unity,Learn,Canvas,Unity UI]
category: [Software]
description: Unity,Learn
---

Canvas（画布）游戏对象是其他Unity UI的基础，其他的Unity UI必须是Canvas（画布）游戏对象的下级游戏对象。

当UI内容发生变化的时候，是以画布为单位进行重绘，合理的将内容分配到不同的画布可以提高性能。

<!-- more -->

### Render Mode（渲染模式）

#### Screen Space Overlay（屏幕空间-覆盖）

屏幕空间-覆盖是根据屏幕分辨率进行渲染，不参考场景中的任何游戏对象或者摄像机，渲染之后将其绘制在其他所有内容之上。

#### Screen Space Camera（屏幕空间-摄像机）

屏幕空间-摄像机是将画布设置为摄像机前方视野中的一个平面。

这种模式下，必须通过Render Camera（渲染摄像机）属性来指定摄像机，且只有在被指定的摄像机中，画布才是可见的。

![Unity2019常用功能:Canvas](/images/20210105-Canvas-01.png)

Plane Distance（平面距离）属性用来指定画布到摄像机的距离，该距离不会影响画布中内容的大小，但是会被距离摄像机更近的其他游戏对象遮挡。如果Plane Distance（平面距离）属性的取值在摄像机Clipping Planes（剪裁平面）属性的取值范围之外，画布仍然是不可见的。

#### World Space（世界空间）

世界空间这种渲染模式是将画布变成了Unity空间的一个普通游戏对象来处理。世界空间这种渲染模式的画布经常做游戏对象的名称或者说明上，如NPC头顶的名称，血条。

![Unity2019常用功能:Canvas](/images/20210105-Canvas-02.png)

### Canvas Group（画布组）

画布组组件是一个需要单独添加的组件，可以对所在画布下的所有UI元素进行统一的设置修改，省去逐一修改设置UI元素的麻烦。可以设置其下UI元素的透明度，是否互动，是否作为射线投射的碰撞体。

> B站视频链接：[https://www.bilibili.com/video/BV1hA411W7Wz/](https://www.bilibili.com/video/BV1hA411W7Wz/)