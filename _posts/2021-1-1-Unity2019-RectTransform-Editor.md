---
layout: post
title: Unity2019常用功能:RectTransform设置
date: 2021-1-1 11:00:05 UTC+8
tags: [Unity,Learn,RectTransform,Unity UI]
category: [Software]
description: Unity,Learn
---

RectTransform矩阵变换主要用于用户界面，和普通游戏对象的Transform区别很大。

RectTransform矩阵变换的Rotation旋转属性和Scale缩放属性和Transform的Rotation旋转属性和Scale缩放属性一样，没有变化。

<!-- more -->

### Pivot 轴心

Pivot轴心属性是以当前游戏对象为坐标系，左下角为（0，0），右上角为（1，1）的一个点。旋转、大小和缩放修改都是围绕Pivot轴心进行的，因此Pivot轴心的位置会影响旋转、大小调整或缩放的结果。

![Unity2019常用功能:RectTransform](/images/20210101-RectTransform-01.png)

### Anchors 锚点

Anchors锚点属性是当前游戏对象以父游戏对象为坐标系，左下角为（0，0），右上角为（1，1）的4个点。这4个点只能形成点，线，或者矩形。表示的时候以左下角的点的坐标为Min（X，Y），右上角的点的坐标为Max（X，Y）来确定4个点在父节点的位置。Anchors锚点在 Scene 视图中显示为四个小三角形控制柄。

![Unity2019常用功能:RectTransform](/images/20210101-RectTransform-02.png)

Anchors锚点属性是当前游戏对象设置位置和大小时候的参照对象，通过设置不同的Anchors锚点属性，参照对象可以是点，线或者矩形。Unity提供了常见的几种锚点设置，即常见的点、线、矩形参照。

![Unity2019常用功能:RectTransform](/images/20210101-RectTransform-03.png)

除了使用官方提供的默认参照方式，也可以通过在【Inspector】检查器窗口修改【Anchors】的值或者在【Scene】场景视图中，鼠标左键点击拖动锚点的标志小三角来设置参照。

![Unity2019常用功能:RectTransform](/images/20210101-RectTransform-04.png)

### 位置字段

RectTransform矩阵变换有5个位置字段，其中，除“Pos Z”字段外，其他4个字段会因为锚点属性的变化而有所不同。	通过设置除“Pos Z”字段外的位置字段，可以设置游戏对象的位置和大小。

“Pos Z”字段可以设置游戏对象的Z轴位置，但是不影响显示顺序。在同一个Canvas画布中，游戏对象的显示顺序由其在【Hierarchy】视图中的顺序决定，下面的游戏对象在前，即下面的游戏对象会遮住上面的游戏对象。

### 设置思路

RectTransform矩阵变化大小和位置受锚点和位置字段属性共同影响，设置的时候，除了本身的结构外，还需要考虑如何能够在屏幕大小、比例发生变化的时候，界面依然保持大致相同或者基本可用。

可以简单的理解为当屏幕发生变化的时候，当前游戏对象的4个角到4个锚点的位置关系不变。

- 当一个游戏对象，长、宽都远小于父游戏对象的时候，比如一些按钮，头像，图标等，可以考虑以距离较近的点作为参照。例如当以个按钮靠近左上的时候，就以左上角作为参照。
- 当一个游戏对象长、宽，其中一个远小于父游戏对象，另外一个超过父游戏对象一半的时候，比如滚动条，底部文字对话框，整行的按钮等，可以考虑以距离较近水平或者垂直线作为参考。
- 当一个游戏对象的长、宽都超过父游戏对象一半的时候，比如背景，外框等，可以考虑以矩形作为参考。

不同的做法实现以后会有不同的效果，都能在一定程度上适应不同大小比例的屏幕。在设计的时候，多使用【Game】窗口的分辨率设置，在目标分辨率下进行设计测试，以保证UI界面的良好可用。

![Unity2019常用功能:RectTransform](/images/20210101-RectTransform-05.png)

> B站视频链接：[https://www.bilibili.com/video/BV1Uf4y1C7v3/](https://www.bilibili.com/video/BV1Uf4y1C7v3/)