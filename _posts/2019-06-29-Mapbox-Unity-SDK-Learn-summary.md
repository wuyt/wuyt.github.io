---
layout: post
title: mapbox-unity-sdk 学习小结
date: 2019-06-29 15:10:05 UTC+8
tags: [Mapbox, Unity3D]
category: [Software]
description: mapbox-unity-sdk学习小结
---

Mapbox不是一个专门的增强现实SDK，是一个移动和网络应用程序的位置数据平台，提供构建基块，将地图，搜索和导航等位置功能。

国内基于地理定位的增强现实开发的时候，其实很麻烦。Google地图的服务器在国外无法访问，百度和高德均未提供Unity的SDK，腾讯地图声称提供了Unity的SDK，但是是针对企业的，普通开发者连长啥样都无法看到。Mapbox提供了Unity的开发包，虽然其数据不够丰富，甚至有大量的缺失，但是在实现某些功能的时候，还是很方便的。

<!-- more -->

## 基本内容

Mapbox官网地址：

https://www.mapbox.cn/

https://www.mapbox.com/

Unity开发包下载地址：

https://www.mapbox.com/install/unity/

当前版本：2.0.0

## 主要功能

Mapbox的主要功能包括地图显示，搜索，定位，导航等。Mapbox还能显示3D地图，自定义地图等内容。

## 支持平台

Mapbox支持苹果安卓和网页端，但是其支持的网页端是直接通过网页开发工具开发的而不是通过Unity发布的。通过Unity只能支持到苹果和安卓。

## 基本结构

![显示地图](/images/2019-6-29-mapbox-unity-sdk-show-map.jpg)

Mapbox中，需要先在Mapbox Studio中定义Datasets地形数据，通过地形数据生成Tilesets瓦片地图，再通过瓦片地图生成Styles样式。

在Unity中，Mapbox提供的Map预制件用来显示地图。其中，通过定义Style URL或者Map Id定义地图的样子，还可以通过Map Id定义的数据，在动态生成3D或其他的内容。

![定位](/images/2019-6-29-mapbox-unity-sdk-location.jpg)

Mapbox提供的Location provider Factory预制件可以实现地图的定位，显示地图及当前位置。比较好的一个地方是Mapbox提供了方便的调试手段，可以在Unity的编辑器中模拟当前的位置和移动。

## 使用示例

![定义database](/images/2019-6-29-mapbox-studio-database.jpg)

在mapbox studio中定义database。database可以定义3种类型的数据，点、线、面。每个数据可以自定义不同的参数。

![定义style](/images/2019-6-29-mapbox-studio-style.jpg)

在mapbox studio中定义style。style是由多个层组成的，这里定义了4个层。

![显示地图](/images/2019-6-29-mapbox-unity-map.jpg)

mapbox unity sdk中，官方的Map预制件（prefab）用于显示地图，通过导入style-url可以显示自定义的地图样子。

![显示地图](/images/2019-6-29-mapbox-unity-map-feature.jpg)

通过对feature的定义，可以根据在mapbox-studio中的database定义的内容，动态生成新的内容。最常用的是根据多边形生成楼房，从而生成3D地图。mapbox还提供了对动态生成内容的修改，可以在动态生成内容上添加脚本或者预制件。

![定义database](/images/2019-6-29-mapbox-unity-location.jpg)

定位功能mapbox也提供了预制件，可以直接使用。很贴心的还提供了在Unity编辑器下进行位置模拟的功能。


