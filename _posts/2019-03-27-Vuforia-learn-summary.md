---
layout: post
title: Vuforia 学习小结
date: 2019-03-27 19:10:05 UTC+8
tags: [AR, Vuforia, Unity3D]
category: [Software]
description: Vuforia 学习小结
---

作为一个老牌的增强现实SDK，相对而言识别效果好，稳定性好。Vuforia Engine是国外使用比较多的一款增强现实SDK，上手简单，可免费使用。虽然官网主要是英文，但是可以搜索到大量的中文教程。

<!-- more -->

## 基本内容

官网地址：https://developer.vuforia.com/

当前版本：8.1.0

![版本功能对照](/images/2019-3-27-vuforia-Version-Info.jpg)

![数据获取](/images/2019-3-27-Vuforia-database-source.jpg)

![基本结构](/images/2019-3-27-Vuforia-structure.jpg)

Vuforia已经集成成为Unity的功能组件，基本功能都可以在菜单里点击。

Key需要输入在“Vuforia Configuration”里

![输入Key](/images/2019-3-27-Vuforia-Set-Key.jpg)

添加“ARCamera”

![添加ARCamera(/images/2019-3-27-Vuforia-ARCamera.jpg)

## 图片识别、方块识别、柱体识别、物体识别、模型识别

![图片识别设置](/images/2019-3-27-Vuforia-Targets.jpg)

识别后的控制

    using UnityEngine;
    
    public class VuforiaTrackableEventHandler : DefaultTrackableEventHandler
    {
    	protected override void Start () {
    		base.Start();
    	}
    
    	/// <summary>
    	/// 发现识别象
    	/// </summary>
    	protected override void OnTrackingFound()
    	{
    		base.OnTrackingFound();
    		Debug.Log(mTrackableBehaviour.TrackableName);
    	}
    	/// <summary>
    	/// 识别对象丢失
    	/// </summary>
    	protected override void OnTrackingLost()
    	{
    		base.OnTrackingLost();
    		Debug.Log(mTrackableBehaviour.TrackableName);
    	}
    }

## 平面认知

平面认知需要“Plane Finder”和“Ground Plane Stage”

![平面认知设置](/images/2019-3-27-Vuforia-Ground-Plane.jpg)

## 视频播放

Vuforia视频播放已经改用Unitiy自带的“Video”组件。

## 关于 Vuforia Object Scanner

- 尽可能选取表面简单，但是有很多花纹图案的物体。因为，Vuforia物体识别本质上是图片识别。
- 物体识别大小要适中，1/4张A4纸到1/2张A4纸大小的东西比较容易识别。
- 扫描的时候，要在光线明亮，背景单一的地方。参考下面官方给出的图片。

![scanner](https://vuforialibrarycontent.vuforia.com/Images/Fall2014/VOS/car.jpg)

![scanner](https://vuforialibrarycontent.vuforia.com/Images/Fall2014/VOS/lighttent.jpg)
