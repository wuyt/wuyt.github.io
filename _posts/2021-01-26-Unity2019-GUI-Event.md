---
layout: post
title: Unity2019常用功能:事件响应
date: 2021-1-26 11:00:05 UTC+8
tags: [Unity,Learn,Event,Unity UI]
category: [Software]
description: Unity,Learn
---

Unity UI的事件响应有两种方式，一种是在编辑器绑定对应事件，一种是完全在脚本中完成。本质上没用区别。

<!-- more -->

Unity UI事件响应都需要一个【EventSystem】游戏对象，如果场景中没用该游戏对象，则UI无法对事件进行响应。在添加Unity UI的时候，如果场景中没用该游戏对象，会自动添加。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-01.png)

### 编辑器设置默认事件响应

**无参数**

```
    public void OnEvent()
    {
        Debug.Log("On Event");
    }
```

选中按钮，点击【On Click()】标签下的【+】，添加一个点击事件的响应。将带有脚本的游戏对象拖到【On Click()】标签下。选择响应的方法是【UIEventLearn】脚本组件的【OnEvent】方法。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-02.png)

**传参数**

如果为方法添加一个参数。

```
    public void OnEvent(string info)
    {
        Debug.Log("On Event "+info);
    }
```

在绑定完响应事件以后，就会有一个输入框提供输入参数。这里的输入框会随参数类型不同而变化。但是最多只能有一个参数。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-03.png)

**联动参数**

部分Unity UI的事件默认包含参数，有些参数可以联动。

```
    public void OnEvent(float info)
    {
        Debug.Log("On Event "+info);
    }
```

选择事件，就会出现2个同名的事件。一个在顶部分割线上的事件是可以联动的事件，另外一个分割线下的是普通事件。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-04.png)

**其他**

有些内容，不需要写脚本，默认事件本身能支持，例如游戏对象的名称等的修改，激活和禁用，发送SendMessage等。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-05.png)

### 编辑器设置事件系统响应

选中一个UI游戏对象，添加一个事件触发器组件。点击【Add New Event Type】按钮，添加对应事件。点击【Pointer Click()】标签下的【+】，添加一个点击事件的响应。将带有脚本的游戏对象拖到【Pointer Click()】标签下。选择响应的方法。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-06.png)

这种方法不光能用在交互的UI游戏对象上，还可以用在普通的UI游戏对象，如Text文本游戏对象和Image图像游戏对象上，还可用于非UI的一些游戏对象的点击上。

### 脚本监听默认事件

```
    public Button button;
    void Start()
    {
        button.onClick.AddListener(OnEvent);
    }
    private void OnEvent()
    {
        Debug.Log("On Event ");
    }
```

在场景中新建一个空的游戏对象，将脚本拖到空的游戏对象上成为其组件。将一个场景中的Button游戏对象拖到脚本组件上为其赋值。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-07.png)

这种方法和在编辑器设置默认事件响应完全一致，只不过是将编辑器中的场景设置搬到了脚本中。下面是箭头函数的写法，脚本绑定到按钮游戏对象本身。

```
    void Start()
    {
        GetComponent<Button>().onClick.AddListener(() =>
        {
            Debug.Log("On Clicked");
        });
    }
```

### 脚本监听事件系统事件

添加一个IPointerClickHandler接口的继承，并实现接口的方法。（如果要监听其他事件，则需要继承并实现其他事件的接口）注意引用UnityEngine.EventSystems。

```
using UnityEngine;
using UnityEngine.EventSystems;
public class UISysEvent : MonoBehaviour, IPointerClickHandler
{
    public void OnPointerClick(PointerEventData eventData)
    {
        Debug.Log("On Click");
    }
}
```

将脚本拖到UI游戏对象下即可。

![Unity2019常用功能:GUI事件响应](/images/2021-1-26-Unity2019-GUI-Event-08.png)

这种方法和在编辑器设置事件系统响应本质上一样，只不过是将编辑器中的场景设置搬到了脚本中。这种方法也可以用于非交互的Unity UI甚至是其他一些非UI的游戏对象。

这种方法和在脚本监听默认事件相比，只能将脚本绑定在要监听的游戏对象上，不能像脚本监听默认事件那样，可以把脚本设置在其他游戏对象上。

> B站视频链接：[https://www.bilibili.com/video/BV1PK4y1s7A7/](https://www.bilibili.com/video/BV1PK4y1s7A7/)