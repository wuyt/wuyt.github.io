---
layout: post
title: EasyAR SDK 学习小结
date: 2019-01-23 12:44:05 UTC+8
tags: [EasyAR Sense, Unity]
category: [blog]
description: EasyAR SDK 学习小结
---

EasyAR是国内的一个增强现实SDK，用起来还算方便，毕竟用中文说明。

<!-- more -->

## 基本内容

官网地址：https://www.easyar.cn/

当前版本：2.3.0

![版本功能对照](/images/2019-01-23-easyar-version-info.jpg)

![基本结构](/images/2019-01-23-easyar-structure.jpg)

图片识别度检测工具：https://www.easyar.cn/targetcode.html

EasyAR常用的都做成了Prefab了，直接使用即可。

Key需要输入在“Tracker”里

![输入Key](/images/2019-01-23-easyar-key-input.jpg)

## 图片识别

![图片识别设置](/images/2019-01-23-easyar-img-set.jpg)

![图片识别数量](/images/2019-01-23-easyar-img-number.jpg)

## 物体识别

物体识别的设置和图片识别设置基本一样。
物体识别需要一组3D模型文件（.obj+.mtl）用于识别，需要另外一组3D模型文件用于识别后的显示。

更多详细说明：
https://www.easyar.cn/doc/EasyAR%20SDK/Guides/EasyAR-3D-Object-Tracking.html

## 视频播放

![视频播放设置](/images/2019-01-23-easyar-video-set.jpg)

视频可以在任意3D物体上播放，也可以播放透明视频。

![视频播放注意事项](/images/2019-01-23-easyar-video-note.jpg)

- 视频播放只能在移动设备上实现
- 对Rendering设置有要求，不能弄错
- 可能会在Unity2018.2版本下播放会黑屏，2018.1版本没问题

## 程序控制

图片识别后的控制例子


    using EasyAR;
    using UnityEngine;
    using UnityEngine.UI;
    
    public class ImageTargetShow : ImageTargetBaseBehaviour
    {
    /// <summary>
    /// 重写Awake事件
    /// </summary>
    protected override void Awake()
    {
    base.Awake();
    
    //订阅事件
    TargetFound += OnTargetFound;   //识别成功事件
    TargetLost += OnTargetLost; //识别对象丢失事件
    TargetLoad += OnTargetLoad; //目标加载事件
    TargetUnload += OnTargetUnload; //目标卸载事件
    }
    
    /// <summary>
    /// 识别成功事件处理方法
    /// </summary>
    void OnTargetFound(TargetAbstractBehaviour behaviour)
    {
    Debug.Log("Found: " + Target.Name); //输出到控制台
    }
    
    /// <summary>
    /// 识别对象丢失事件处理方法
    /// </summary>
    void OnTargetLost(TargetAbstractBehaviour behaviour)
    {
    Debug.Log("Lost: " + Target.Name);  //输出到控制台
    }
    
    /// <summary>
    /// 识别对象加载事件处理方法
    /// </summary>
    void OnTargetLoad(ImageTargetBaseBehaviour behaviour, ImageTrackerBaseBehaviour tracker, bool status)
    {
    Debug.Log("Load target (" + status + "): " + Target.Id + " (" + Target.Name + ") " + " -> " + tracker);
    }
    
    /// <summary>
    /// 识别对象卸载事件处理方法
    /// </summary>
    void OnTargetUnload(ImageTargetBaseBehaviour behaviour, ImageTrackerBaseBehaviour tracker, bool status)
    {
    Debug.Log("Unload target (" + status + "): " + Target.Id + " (" + Target.Name + ") " + " -> " + tracker);
    }
    }
    

视频播放控制例子

    using EasyAR;
    using UnityEngine;
    
    public class VideoPlayerController : VideoPlayerBaseBehaviour
    {
    private System.EventHandler videoReayEvent;
    private System.EventHandler videoErrorEvent;
    private System.EventHandler videoReachEndEvent;
    
    /// <summary>
    /// 重写Awake事件
    /// </summary>
    protected override void Awake()
    {
    base.Awake();
    }
    
    /// <summary>
    /// 重写Start事件
    /// </summary>
    protected override void Start()
    {
    videoReayEvent = OnVideoReady;
    videoErrorEvent = OnVideoError;
    videoReachEndEvent = OnVideoReachEnd;
    base.Start();
    //添加事件订阅
    VideoReadyEvent += videoReayEvent;  //视频加载成功事件
    VideoErrorEvent += videoErrorEvent; //视频加载失败事件
    VideoReachEndEvent += videoReachEndEvent;   //视频播放完成事件
    Open();
    }
    
    /// <summary>
    /// 视频加载成功事件
    /// </summary>
    void OnVideoReady(object sender, System.EventArgs e)
    {
    Debug.Log("Load video success");
    }
    
    /// <summary>
    /// 视频加载失败事件
    /// </summary>
    void OnVideoError(object sender, System.EventArgs e)
    {
    Debug.Log("Load video error");
    }
    
    /// <summary>
    /// 视频播放完成事件
    /// </summary>
    void OnVideoReachEnd(object sender, System.EventArgs e)
    {
    Debug.Log("video reach end");
    }
    
    /// <summary>
    /// 重写OnDestory事件
    /// </summary>
    protected override void OnDestroy()
    {
    VideoReadyEvent -= videoReayEvent;
    VideoErrorEvent -= videoErrorEvent;
    VideoReachEndEvent -= videoReachEndEvent;
    Close();
    base.OnDestroy();
    }
    
    /// <summary>
    /// 视频播放
    /// </summary>
    public void VideoPlay()
    {
    Play();
    }
    
    /// <summary>
    /// 视频停止
    /// </summary>
    public void VideoStop()
    {
    Stop();
    }
    
    /// <summary>
    /// 视频暂停
    /// </summary>
    public void VideoPause()
    {
    Pause();
    }
    }


