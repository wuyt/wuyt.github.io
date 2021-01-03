---
layout: post
title: Unity2019常用功能:RectTransform脚本控制
date: 2021-1-3 11:00:05 UTC+8
tags: [Unity,Learn,RectTransform,Unity UI,Script]
category: [Software]
description: Unity,Learn
---

RectTransform设置游戏对象大小位置的时候，不仅在Unity编辑器中与Transform不一样，程序控制上也不一样。

RectTransform作为一个组件存在于游戏对象上，所有控制方法和属性都在该组件下。

RectTransform下的rect类可以获取游戏对象的宽（rect.width）和高（rect.height），但是不可以直接设置。

<!-- more -->

### Pivot 轴心和 Anchors 锚点

RectTransform类下的pivot属性可以用于获取和设置游戏对象的轴心。

RectTransform类下的anchorMin和anchorMax属性可以用于获取和设置游戏对象的锚点。

通常修改轴心或者锚点都会让UI的位置或大小发生变化。

### offset 锚点偏移

锚点偏移是2个矢量，一个是从左下角的锚点到游戏对象的左下角，一个是从右上角的锚点到游戏对象的右上角。无论当前锚点是形成点，线或者矩形，都能通过这样2个矢量来设置游戏对象的位置和大小。

![Unity2019常用功能:RectTransform](/images/20210103-RectTransform-01.png)

### SetSizeWithCurrentAnchors

offset锚点偏移用于定位游戏对象比较方便，如果只是设置大小会略显麻烦，特别是在游戏对象进行大小变化的是。这个时候推荐使用SetSizeWithCurrentAnchors方法来设置大小。

SetSizeWithCurrentAnchors方法的第一个参数是选择设置宽（RectTransform.Axis.Horizontal）还是高（RectTransform.Axis.Vertical），第二个参数是具体大小。

```
rectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Horizontal, 200);
rectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Vertical, 100);
```

### anchoredPosition

anchoredPosition属性是一个矢量，通过该矢量可以获取及设置当前游戏对象的位置。

首先，根据游戏对象的轴心，计算出在锚点矩阵中的参考点位置。

- 如果是矩阵，则参考点到轴心的矢量即为anchoredPosition。
- 如果是线段，则锚点矩阵减少一个维度后，参考点的对应位置到轴心的矢量即为anchoredPosition。
- 如果是点，则是从锚点到轴心的矢量即为anchoredPosition。

![Unity2019常用功能:RectTransform](/images/20210103-RectTransform-02.png)

### SetInsetAndSizeFromParentEdge

SetInsetAndSizeFromParentEdge方法是以父游戏对象的上、下、左、右4个点中的一个作为参照，同时设置游戏对象到该点的距离和对应方向上的值。

![Unity2019常用功能:RectTransform](/images/20210103-RectTransform-03.png)

### 简单总结

- 在程序中，修改轴心和锚点比较容易，只是修改完以后，都需要重新设置一下游戏对象的大小和位置。
- offset锚点偏移设置位置和大小比较方便，但是如果要实现移动或者变形动画就比较麻烦。
- 变形推荐使用SetSizeWithCurrentAnchors方法，移动推荐使用anchoredPosition属性，因为这2种做法和锚点无关，在任何情况下都能使用。
- SetInsetAndSizeFromParentEdge可以同时设置位置和大小，但是会修改锚点。仅推荐游戏对象原有参考本身就是父游戏对象4边中间的点的时候使用。


> B站视频链接：[https://www.bilibili.com/video/BV1kh41117xH/](https://www.bilibili.com/video/BV1kh41117xH/)