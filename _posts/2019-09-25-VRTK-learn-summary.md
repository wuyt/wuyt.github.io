---
layout: post
title: VRTK学习小结
date: 2019-09-25 21:10:05 UTC+8
tags: [Unity]
category: [blog]
description: VRTK学习小结
---

VRTK全程Virtual Reality Toolkit，是国外的一个VR开发工具，其最大的特点是支持主流的多个VR SDK，包括SteamVR、Oculus、GearVR等。VRTK屏蔽了各个不同VR SDK的差异，能够做到一次开发就能在多个不同的VR设备上使用。

其次，VRTK提供了比官方更丰富的示例，并且提供了模拟器，让开发者能够更方便的开发VR内容。

<!-- more -->

### 下载

VRTK可以在Unity商城中直接下载。

VRTK的官网地址：https://www.vrtk.io/

### 基本结构

VRTK的中心脚本是“VRTK_SDK Manager”脚本。这个脚本所在游戏对象就是场景中玩家所在位置，包括Camera。

“VRTK_SDK Manager”脚本所在游戏对象下，是“VRTK_SDK Steup”脚本所在的游戏对象。“VRTK_SDK Steup”脚本设置具体的VR SDK，并将对应的内容设置为其子游戏对象。当需要同时针对多个VR SDK的时候，需要多个“VRTK_SDK Steup”脚本游戏对象。

VRTK靠“VRTK_Controller Events”脚本响应手柄的按键，需要根据手柄添加“VRTK_Controller Events”脚本游戏对象。


![VRTK基本结构](/images/2019-9-25-VRTK-basic-structure.jpg)

### 手柄射线

手柄射线是通过添加“VRTK_Pointer”脚本，并添加射线类型脚本实现的，被指示物体必须包含“Collider”组件。通常指示之后会需要物体边框高亮，需要响应“DestinationMarker”事件，VRTK提供了物体边框高亮的脚本。

![VRTK手柄射线](/images/2019-9-25-VRTK-point.jpg)

### 传送

VRTK提供了3种传送方式。“Basic”是最基础简单的模式，但是有个限制，只能在同一个水平面传送，无法实现类似上楼梯的效果。“Height Adjust”高度调整模式可以在不同平面传送。“Dash”模式不是传送是快速移动过去，有点类似魔兽世界里战士冲锋的技能，在模拟器上看挺好玩，估计到了设备上很多人都会晕的，大概在特定的情景才能用到。

![VRTK传送](/images/2019-9-25-VRTK-teleport.jpg)

### 与物体交互

与物体交互分为3种基础类型：触碰、拾取和使用。其中，触碰是另外2种的基础。

![VRTK传送](/images/2019-9-25-VRTK-interact.jpg)

### UI

VRTK操作Unity UI很容易，在手柄添加对应的组件，然后在Canvas中添加“VRTK_UI Canvas”组件即可。

![VRTK传送](/images/2019-9-25-VRTK-UI.jpg)