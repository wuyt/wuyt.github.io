---
layout: post
title: Unity AssetBundle
date: 2019-12-20 19:10:05 UTC+8
tags: [ Unity]
category: [blog]
description: Unity AssetBundle
---

AssetBundle是Unity提供的一种存档文件，其中包含了可以在运行时加载的用于特定平台的非代码资源。可用于下载内容，减小初始安装大小，加载针对特定平台的优化过的资源以及减轻运行时内存压力。

<!-- more -->

![AssetBundle技能树](/images/2019-12-20-AssetBundle-skill-tree.jpg)

### 基础信息

![AssetBundle基础信息](/images/2019-12-20-AssetBundle-Base.jpg)

##### 官方教程
https://learn.unity.com/tutorial/assets-resources-and-assetbundles
https://docs.unity3d.com/Manual/AssetBundlesIntro.html


### 资源打包

![AssetBundle资源打包](/images/2019-12-20-AssetBundle-Build.jpg)

### 打包策略

![AssetBundle打包策略](/images/2019-12-20-AssetBundle-packaging-strategy.jpg)

### 打包工具

Unity提供了一个打包工具Asset Bundle Browser tool，可以通过Package Manager安装，也可以通过GitHub下载。
https://github.com/Unity-Technologies/AssetBundles-Browser

### 脚本

##### 打包

BuildPipeline.BuildAssetBundles
打包

##### 加载包

AssetBundle.LoadFromMemory（Async）
从内存加载，不推荐使用，UnityWebRequest使用加密下载数据并需要从未加密的字节创建AssetBundle时，此功能很有用。

AssetBundle.LoadFromFile（Async）
从文件加载，效果最好

AssetBundleDownloadHandler
最常用

##### 加载资源

LoadAllAssets
加载超过2/3内容

LoadAsset
加载少量单个

LoadAssetWithSubAssets
包含多个嵌入对象

##### 卸载包

AssetBundle.Unload(true);
推荐，卸载所有内容

AssetBundle.Unload(false);
容易产生重复加载，Resources.UnloadUnusedAssets清除引用

##### 加载依赖

AssetBundleManifest.GetAllDependencies
加载所有依赖

AssetBundleManifest.GetDirectDependencies
加载直接子集依赖