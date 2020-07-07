---
layout: post
title: EasyAR Sense 4.0 Sparse Spatial Map supports simultaneous loading of multiple maps
date: 2020-06-02 11:00:05 UTC+8
tags: [EasyAR Sense, Unity]
category: [blog]
description: Unity,EasyAR
---

When multiple Sparse Spatial Map are used, the structure is actually that there are multiple Sparse Spatial Map game objects in the scene, and each game object corresponds to a specific sparse space map.

<!-- more -->

![Use structure](/images/20200629-ssm-01.jpg)

The code is also not complicated, set the ID, name and other settings of each SparseSpatialMap. Then use the .Localizer.startLocalization() method of SparseSpatialMapWorkerFrameFilter for localization.

```
//get map information，list is a list of map information strings
var list = game.LoadMapInfos();
mapStatus = new string[list.Count];

for (int i = 0; i < list.Count; i++)
{
    var info = list[i].Split(',');
    var map = Instantiate(prefab);//Generate Sparse Spatial Map
    map.SourceType = SparseSpatialMapController.DataSource.MapManager;
    map.MapManagerSource.ID = info[0];//Set map ID
    map.MapManagerSource.Name = info[1];//Set map name
    map.MapWorker = mapWorker;

    //Map loading event
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
    //Locate successful event
    map.MapLocalized += () =>
    {
        text.text = map.MapInfo.Name+"-->"+"Localized."+Environment.NewLine+text.text;
    };
    //Stop positioning event
    map.MapStopLocalize += () =>
    {
        text.text = map.MapInfo.Name+"-->"+"Stopped."+Environment.NewLine+text.text;
    };
}
//Start localizing the map
mapWorker.Localizer.startLocalization();
```

You can load multiple sparse spatial maps at the same time, but at the same time, only one map can be localized (MapLocalized).

When loading, the MapLoad events of all maps are triggered immediately, but only one map's MapLocalized event can be triggered. Once other maps trigger the MapLocalized event, the MapStopLocalize of the previous map must be triggered.