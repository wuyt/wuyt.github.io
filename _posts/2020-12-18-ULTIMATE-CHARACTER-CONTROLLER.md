---
layout: post
title: Ultimate Character Controller
date: 2020-12-18 11:00:05 UTC+8
tags: [Unity,Plugins,FPS]
category: [Software]
description: Unity,Plugins
---

Ultimate Character Controller是Opsive推出的一个针对FPS类游戏的开发插件，这个插件可以在Unity平台下通过相对简单的配置，快速的搭建出一个FPS游戏。官方提供了还算详细的使用说明和视频教程，虽然都是英文的，基本能够更着走。

![Ultimate Character Controller](/images/20201218-UCC-01.jpg)

<!-- more -->

## 基本功能

Ultimate Character Controller的基本功能包括

- 第一人称视角/第三人称视角玩家控制，还有一些奇怪的视角。
- 可以配置近身武器（刀剑），远程武器（弓箭，枪械），投掷武器（手榴弹），魔法攻击。
- 可以设置击中效果（弹孔），不同地形走路效果（脚印，脚步声）等。
- 可以拾取/丢弃物品，回血，加速等。但是，没有背包。
- 可以使用载具（车，马）。

导入Ultimate Character Controller以后，有Demo能比较直观了解其功能。

[Demo演示](https://www.bilibili.com/video/BV1Ev411k7US/)

## 相关插件

**FPS Mesh Tool**

FPS Mesh Tool是一个分割模型用的工具。Ultimate Character Controller的第一人称视角需要将玩家控制的人物模型的手部单独拿出来使用。很多导入的模型并没有这么设置，所以，需要使用这个工具来重新分割模型，使其能适用于Ultimate Character Controller。

![Ultimate Character Controller](/images/20201218-UCC-02.jpg)

**Behavior Designer**

当需要实现NPC的AI的时候，官方提供了接口。不过官方推荐的是Behavior Designer，毕竟是自家的东西。而且有对应的示例。

![Ultimate Character Controller](/images/20201218-UCC-03.jpg)

**Behavior Designer – Movement Pack**

这个插件是实现NPC自动寻路的，配合上Unity默认的寻路功能，即可实现NPC自动寻路。当然，也可以和其他寻路插件配合。

![Ultimate Character Controller](/images/20201218-UCC-04.jpg)

**Deathmatch AI Kit**

这个是专门用于配置NPC的AI的插件，刚推出，还没进入到Unity的商城。不过这个的使用需要配合Behavior Designer和Behavior Designer – Movement Pack。看了说明，似乎配置起来也还是方便的。至少比学习使用行为树插件简单。

![Ultimate Character Controller](/images/20201218-UCC-05.jpg)

## 使用感受

简单的使用了一下，

如果一个完全不懂Unity的人想要通过这个插件配置出一个FPS游戏，很困难，不太靠谱。使用者至少还是需要有Unity的基础知识才行。

可以配置的项目蛮多的，兼容或者说还是比较灵活能满足很多场景下的使用。

学习难度不算低，因为资料比较少，基本上只有官方的视频和文档作为参考。

## 其他

其实，Unity商城里面类似的，专门配置游戏插件还有好几个，可以通过配置来自己做出游戏。

对于一些想做个游戏的人有很大帮助，当然，共同的难点都是，基本只有官方文档和视频作为学习资料，而且还都是英文的。

## Ultimate Character Controller视频

官方网站：https://opsive.com/

官网视频搬运：https://www.bilibili.com/video/BV1Dh411Z7rW/

简单教程：

- [01-基本设置和Demo](https://www.bilibili.com/video/BV1Ev411k7US/)
- [02-第一人视角角色添加](https://www.bilibili.com/video/BV1HV41127RQ/)
- [02-添加玩家](https://www.bilibili.com/video/BV1iV41127cR/)
- [03-添加物品](https://www.bilibili.com/video/BV1ot4y1v76s/)
- [04-添加设置近战武器](https://www.bilibili.com/video/BV1By4y1C7Jy/)
- [04-近战武器设置补充](https://www.bilibili.com/video/BV1Fy4y187BA/)
- [05-NPC的AI](https://www.bilibili.com/video/BV1Rt4y1v7Rw/)
- [06-添加设置徒手攻击](https://www.bilibili.com/video/BV1nr4y1w7sB/)
- [07-添加枪械](https://www.bilibili.com/video/BV1eK4y1Z7Ct/)
- [08-拾取物品和人物复活](https://www.bilibili.com/video/BV13K411P783/)
- [09-AI敌人修改](https://www.bilibili.com/video/BV1Yi4y1L7iY/)
- [10-简单使用总结](https://www.bilibili.com/video/BV1Pz4y1r738/)