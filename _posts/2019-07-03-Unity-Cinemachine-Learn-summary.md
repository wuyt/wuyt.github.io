---
layout: post
title: Unity Cinemachine 学习小结
date: 2019-07-03 15:10:05 UTC+8
tags: [Unity3D, Cinemachine]
category: [Software]
description: Unity Cinemachine 学习小结
---

CinemaChine是Unity官方推出的一个免费的camera资源。虽然配置起来略显复杂，但是很好的解决了原有的camera功能单一使用不方便的问题。

CinemaChine的功能非常强大，提供了镜头跟随，鼠标控制镜头方向转动，镜头在轨道上移动，同时跟踪多个目标，多个镜头切换等功能。

<!-- more -->

## 基本内容

Cinemachine是Unity官方推出的资源，所以在Unity的商城中直接搜索就可以找到。
导入以后，在Cinemachine目录中，有pdf格式的文档，虽然是英文的，但是很详细。另外，在该目录中还有一个unitypackage文件，点击后可以导入官方的示例。

## 基本结构

![基本结构](/images/2019-7-3-cinemachine.jpg)

Cinemachine本身不替代camera，所以，场景中必须有一个camera。Cinemachine需要在camera上添加一个【Cainemachine Brain】的组件，同时，实际镜头所在的位置是由【Virtual Camera】提供。【Cainemachine Brain】处理多个【Virtual Camera】之间的切换关系，【Virtual Camera】提供具体显示内容的来源。

Virtual Camera中最重要的属性有下面几个

- Priority：优先级。当场景中有多个Virtual Camera的时候，数字大的优先显示。
- Follow：设置当前Virtual Camera运动的参照目标。
- Looke At：设置当前Virtual Camera镜头对准的目标。
- Body：设置当前Virtual Camera运动的特性。
- Aim：设置当前Virtual Camera镜头对准的特性。

Body的控制方式官方提供了以下几种：

- Do nothing：无控制。
- Framing Transposer：在屏幕空间中计算相机和目标的Offset，不需要【Looke At】对象。
- Hard Lock To Target：把相机和目标的位置和朝向进行绑定，常用于第一人称模式。
- Orbital Transposer：将镜头限制在一个圆形轨道上，用输入控制其移动。
- Tracked Dolly：将镜头限制在自定义轨道上，根据【Follow】对象的移动来移动。
- Transposer：基本形式，根据【Follow】对象的移动来移动。

Aim的控制方式官方提供了以下几种：

- Do nothing：不控制。
- Composer：跟踪一个目标。
- Group Composer：跟踪多个目标。
- Hard Look At：跟踪一个目标，不可调，相当于LookAt语句效果。
- POV：用输入来控制镜头方向。
- Same As Follow Object：跟随拍摄模式。

## 官方提供的Camera

- FreeLookAt Camera：这个是会在目标物体周围生成三个轨道，通过输入控制镜头的移动，实现围绕目标进行观察的效果。
- Blend List Camera：多个镜头根据时间进行切换。
- State-Driven Camera：根据动画状态切换镜头
- ClearShot Camera：根据跟踪对象被拍摄的效果切换镜头
- Dolly Camera with Track：在自定义轨道上的镜头
- Target Group Camera：同时追踪多个目标
- Mixing Camera：在指定的两个镜头中间某个位置的镜头