---
layout: post
title: EasyAR4多个稀疏空间地图的使用
date: 2020-06-02 11:00:05 UTC+8
tags: [Unity,EasyAR,Sparse Spatial Map]
category: [Software]
description: Unity,EasyAR
---

EasyAR4的稀疏空间地图支持同时加载多个稀疏空间地图并使用。

<!-- more -->

![使用结构](/images/20200629-ssm-01.jpg)

多个稀疏空间地图使用时候结构其实就是在场景中有多个SparseSpatialMap游戏对象，每个游戏对象对于一个具体的稀疏空间地图。

从代码上也不复杂，设置每个SparseSpatialMap的ID，名称，事情和其他设置。然后，统一用SparseSpatialMapWorkerFrameFilter的.Localizer.startLocalization()方法进行本地化即可。

```
//获取地图信息，list是地图信息字符串列表
var list = game.LoadMapInfos();
mapStatus = new string[list.Count];

for (int i = 0; i < list.Count; i++)
{
    var info = list[i].Split(',');
    var map = Instantiate(prefab);//生成稀疏空间地图
    map.SourceType = SparseSpatialMapController.DataSource.MapManager;
    map.MapManagerSource.ID = info[0];//设置地图ID
    map.MapManagerSource.Name = info[1];//设置地图名称
    map.MapWorker = mapWorker;

    //地图加载事件
    map.MapLoad += (mapInfo, isSuccess, error) =>
    {
        if (isSuccess)
        {
            text.text = mapInfo.Name + "-->" + "map load success." + Environment.NewLine + text.text;
        }
        else
        {
            text.text = mapInfo.Name + "-->" + "map load fail." + Environment.NewLine + text.text;
        }
    };
    //定位成果事件
    map.MapLocalized += () =>
    {
        text.text = map.MapInfo.Name+"-->"+"Localized."+Environment.NewLine+text.text;
    };
    //停止定位事件
    map.MapStopLocalize += () =>
    {
        text.text = map.MapInfo.Name+"-->"+"Stopped."+Environment.NewLine+text.text;
    };
}
//开始本地化地图
mapWorker.Localizer.startLocalization();
```

使用效果，可以同时加载多个稀疏空间地图，但是，同一时间，只有一个地图可以定位（MapLocalized）。

加载的时候，所有地图的MapLoad事件都马上触发，但是，只有一个地图的MapLocalized事件能被触发。一旦其他地图触发MapLocalized事件，之前地图的MapStopLocalize必定被触发。