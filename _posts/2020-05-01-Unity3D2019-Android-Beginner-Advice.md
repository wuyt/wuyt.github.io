---
layout: post
title: Unity2019安卓平台新手建议
date: 2020-05-29 11:00:05 UTC+8
tags: [Unity]
category: [blog]
description: Unity,Android
---

给新手的Unity2019安卓平台建议

<!-- more -->

# 第一次安装

对于初学者，建议一定使用Unity Hub进行安装。Unity Hub下载地址：[https://unity.cn/releases](https://unity.cn/releases)


![下载Unity Hub](/images/20200529-Unity2019Android-01.jpg)

安装完Unity Hub以后，安装Unity2019。

Unity安装目录，项目目录，发布APK的目录，最好都没有中文，否则容易出错。

![安装Unity](/images/20200529-Unity2019Android-02.jpg)

第一次安装的Unity2019的安卓平台内容，一定要选上【Android SDK & NDK Tools】和【OpenJDK】。

![安装Unity](/images/20200529-Unity2019Android-03.jpg)

安装完成以后，新建一个项目，打开Unity2019。在【Preferences】窗口的【External Tools】里面能看见JDK、ADK和NDK的安装情况。如果这里显示错误，需要重新安装【Android SDK & NDK Tools】和【OpenJDK】。

![安装Unity](/images/20200529-Unity2019Android-04.jpg)

Unity2019默认只能打包Android 9.0（29）的APK，此时打包其他版本的会有下面的提示

UnityException: Target Android SDK not installed

Android SDK does not include your Target SDK of 27. 

![安装Unity](/images/20200529-Unity2019Android-05.jpg)

# 复制JDK和Android SDK

为了以后少安装3G的文件和能够打包其他版本的APK，做下面的操作。

打开JDK、Android SDK所在目录。

![复制JDK和Android SDK](/images/20200529-Unity2019Android-06.jpg)

将其复制到一个新的目录中。

![复制JDK和Android SDK](/images/20200529-Unity2019Android-07.jpg)

# 配置Java环境

为了升级Android SDK，本地需要有Java环境。打开命令提示符。

![配置Java环境](/images/20200529-Unity2019Android-08.jpg)

输入“java -version”就能知道本地是否有Java环境。

![配置Java环境](/images/20200529-Unity2019Android-09.jpg)

如果没有Java环境，进行以下操作。另外，Unity打包用的Java版本，最好是1.8，已知1.12会出错。

在【我的电脑】上点鼠标右键，属性。

![配置Java环境](/images/20200529-Unity2019Android-10.jpg)

打开环境变量设置，添加系统变量“JAVA_HOME”，目录指向复制出来的“OpenJDK”的目录。

![配置Java环境](/images/20200529-Unity2019Android-11.jpg)

修改【CLASSPATH】变量，添加“%JAVA_HOME%\bin”和“%JAVA_HOME%\lib”。

![配置Java环境](/images/20200529-Unity2019Android-12.jpg)

修改【Path】变量，添加“%JAVA_HOME%\bin”和“%JAVA_HOME%\lib”。

![配置Java环境](/images/20200529-Unity2019Android-13.jpg)

这样，Java环境就配置完成。

![配置Java环境](/images/20200529-Unity2019Android-14.jpg)

# 升级Android SDK

打开命令提示符，到Android SDK目录下的【tools\bin】目录。

![升级Android SDK](/images/20200529-Unity2019Android-15.jpg)

运行“sdkmanager --list”可以查看当前Android SDK的内容。

![升级Android SDK](/images/20200529-Unity2019Android-16.jpg)

需要安装的包也在列表中。

![升级Android SDK](/images/20200529-Unity2019Android-18.jpg)

运行“sdkmanager XXXX”可以按照对应的包，运行“sdkmanager --uninstall XXXX”可以卸载对应的包。

![升级Android SDK](/images/20200529-Unity2019Android-17.jpg)

安装到23及Android 6.0就基本可以覆盖大多数设备。

![升级Android SDK](/images/20200529-Unity2019Android-19.jpg)

# 配置Unity2019

打开【Preferences】窗口的【Extenal Tools】标签，设置JDK和Android SDK目录。

![配置Unity2019](/images/20200529-Unity2019Android-20.jpg)

之后，再安装Unity2019就可以不安装【Android SDK & NDK Tools】和【OpenJDK】了。

![配置Unity2019](/images/20200529-Unity2019Android-21.jpg)

第一次打包的时候，会需要连接互联网。

![配置Unity2019](/images/20200529-Unity2019Android-22.jpg)

这个时候，如果卡住，解决方法参考[https://blog.csdn.net/qq_14838361/article/details/100011804](https://blog.csdn.net/qq_14838361/article/details/100011804)