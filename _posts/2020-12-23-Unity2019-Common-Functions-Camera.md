---
layout: post
title: Unity2019常用功能:Camera摄像机
date: 2020-12-23 11:00:05 UTC+8
tags: [Unity,Learn,Camera]
category: [Software]
description: Unity,Learn
---

Camera摄像机游戏对象是Unity场景中最重要的游戏对象。每个场景至少需要一个激活的Camera摄像机游戏对象，否则无法显示。玩家或者用户能看到的内容都是通过Camera摄像机游戏对象来展示的。添加或者新建场景以后，默认都会有一个名叫【Main Camera】的Camera摄像机游戏对象。

<!-- more -->

### Projection 投影

Unity的Camera提供了2种投影模式，Perspective透视模式Orthographic正交模式。

透视模式是近大远小的模式。

![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-02.jpg)

正交模式是远近一样大的模式，常用于2D。

![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-03.jpg)

### Field of View 视野

Field of View 视野可以设置视野的夹角，默认为60度，和人眼的舒适视野基本一致。常用于望远镜、瞄准镜、小地图的制作。

### Clipping Planes 剪裁平面

Clipping Planes剪裁平面用于设置摄像机看的距离，默认为0.3-1000。简单说就是只能看到距离0.3米-1000米范围内的东西，太近了看不到，太远了也看不到。

### Clear Flags清除标识

Clear Flags清除标识是用于处理屏幕没有渲染的部分显示什么内容。默认为Skybox天空盒。

- Skybox天空盒是默认选项，会显示一个类似天空的效果，在通常的3D场景中使用很多。
- Solid Color是纯色，选中以后，可以通过下面的Background属性来设置具体的颜色。通常用在界面，2D内容中。
- Depth only是仅有深度，简单说就是背景透明，通常是在场景中有多个摄像机的时候才使用。
- Don’t Clear不清除，不处理没有渲染的部分。通常不会用到。

### Culling Mask剔除遮罩

Culling Mask剔除遮罩可以根据游戏对象的Layer图层决定是否显示该游戏对象。默认为全部都显示。

设置Culling Mask剔除遮罩
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-04.jpg)

设置Layer图层
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-05.jpg)

显示效果
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-06.jpg)

### Depth 深度

Depth 深度用于设置多个摄像机的显示顺序，数值大的显示在前面，数值小的显示在后面。数值相同的时候，在Inspector层级视图中，下面的显示在前面。

### Viewport Rect

Viewport Rect 用于设置显示范围。“X，Y”是起始坐标，取值范围是0-1，屏幕左下角为“0”，右上角为“1”。“W，H”是高和宽，取值范围是0-1。

Viewport Rect和Depth常用于多个摄像机同时使用时候的设置。

主视角摄像机
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-07.jpg)

地图显示摄像机
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-08.jpg)

显示效果
![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-09.jpg)

### MainCamera标签

场景默认的摄像机Main Camera游戏对象的Tag标签默认值为“MainCamera”。Tag标签为“MainCamera”的摄像机并且激活时，可以在脚本中用“Camera.main”的方式直接获取。而之后添加的摄像机，默认的Tag标签都是“Untagged”。

![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-10.jpg)

### Audio Listener

通过直接添加游戏对象添加出来的摄像机游戏对象，默认带有“Audio Listener”组件。该组件的是判断声音源方向和距离的参照。

![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-11.jpg)

每个场景中，只能有一个被激活的“Audio Listener”组件，否则运行时会不停的有消息提示。所以，当场景中有多个摄像机游戏对象时，必须删除或禁用多余的“Audio Listener”。

![Unity2019常用功能:Camera摄像机](/images/20201223-Camera-12.jpg)

> B站视频链接：https://www.bilibili.com/video/BV1fi4y1c7QQ/