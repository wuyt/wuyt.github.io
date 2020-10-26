---
layout: post
title: Unity与浏览器脚本交互
date: 2019-11-29 21:10:05 UTC+8
tags: [Browser scripts,  Unity3D]
category: [Software]
description: Unity与浏览器脚本交互
---

Unity发布成WebGL之后，可以与浏览器脚本进行交互，
官方说明链接：https://connect.unity.com/doc/Manual/webgl-interactingwithbrowserscripting

<!-- more -->

### 浏览器脚本调用Unity方法

在浏览器脚本中，支持调用Unity的方法，提供了和Unity中一样的SendMessage方法。
SendMessage(脚本所在游戏对象, 要调用的方法, 参数);
在浏览器脚本中，直接调用即可。

``` Javascript
  <script>
    var gameInstance = UnityLoader.instantiate("gameContainer", "Build/ShimaRinWeb.json", { onProgress: UnityProgress });
    function SendToUnity() {
      var info = document.getElementById("SendText");
      gameInstance.SendMessage('GameMaster', 'GetFromHtml', info.value);
    }
  </script>
```

### Unity调用浏览器脚本方法

之前Unity提供的Application.ExternalCall方法现在已经被设为过时。
现在需要用到的方法是在Plugins目录下添加“*.jslib”文件，将浏览器脚本写在里面。
脚本格式如下。需要注意的是，Unity发送过去的信息需要经过转换才行。

``` Javascript
mergeInto(LibraryManager.library, {
  GetFromUnity: function (info) {
    document.getElementById("ShowInfo").value=UTF8ToString(info);
  },
});
```

在Unity中用“DllImport”注解引入方法即可

``` c#
[DllImport("__Internal")]
private static extern void GetFromUnity(string info);

public void SendToHtml()
{
    GetFromUnity(inputField.text);
}
```

### 其他注意内容

Unity发布的WebGL会将键盘输入截取，导致只能在Unity生成的画布中输入，无法在浏览器其他地方进行输入。
Unity提供了“WebGLInput.captureAllKeyboardInput”属性，当该属性为“false”的时候，即可在浏览器其他地方输入，默认值为“true”。

这里做了个Demo，地址如下，访问速度略慢，见谅。
http://www.nshworkshop.cn/unityweb/