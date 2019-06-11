---
layout: post
title: Unity NavMeshComponents 学习小结
date: 2019-06-11 10:10:05 UTC+8
tags: [Unity3D, NavMeshComponents]
category: [Software]
description: Unity NavMeshComponents 学习小结
---

NavMeshComponents是Unity官方提供的一个自动寻路的一个扩展，基于Unity本身的寻路功能，只是更加便于使用而已。

<!-- more -->

下载地址：

https://github.com/Unity-Technologies/NavMeshComponents

下载下来的是一个Unity的项目而不是导入包，里面有官方的例子，实际使用到的只是“NavMeshComponents”目录。

![基本结构](/images/2019-6-11-NavMeshComponents-structure.jpg)

NavMeshSurface：提供寻路功能的基本设置及静态烘培。

NavMeshAgent：提供移动对象基本设置。

NavMeshSurface和NavMeshAgent是通过“Agent Type”进行对应的，不同的移动对象需要烘培不同的NavMesh。

NavMeshModifier：用于设置场景中的固定障碍物或特殊路径的。这个组件可以影响到其所在游戏对象的子对象。

NavMeshLink：用于在没有路径的地方做连接，使移动对象能够通过，例如小的沟壑，爬楼等。

NavMeshObstacle：用来设置场景中活动的障碍物。使用略微复杂，请直接查看官网说明。

总结，使用起来还算方便，虽然不够完美但一般场景使用足够了。

