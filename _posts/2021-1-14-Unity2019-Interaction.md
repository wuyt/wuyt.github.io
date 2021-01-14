---
layout: post
title: Unity2019常用功能:交互游戏对象
date: 2021-1-14 14:00:05 UTC+8
tags: [Unity,Learn,Interaction,Unity UI]
category: [Software]
description: Unity,Learn
---

交互游戏对象是官方提供的一组用户界面常用的一些交互的游戏对象，包括Button按钮，Toggle开关，Slider滑动条，Scrollbar滚动条，Dropdown下拉选单和Input Field输入字段。

<!-- more -->

### Interactable（交互）选项

Interactable选项默认选中，即可以进行交互。当去掉选项以后，则不可以交互，即不可以进行点击，输入，或者修改。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-01.png)

### Transition（过渡）选项

Transition选项可以让交互游戏对象在不同状态显示效果不同，让使用者明确知道自己在操作哪个UI元素。Transition选项有4种选项，None无效果，Color Tint颜色变化，Sprite Swap图片切换，Animation动画效果。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-02.png)

### Button（按钮）

Button的本身样子是由一个Image（图像）游戏对象和一个Text（文本）游戏对象组成，按钮显示文字通过修改Button游戏对象的子游戏对象Text中的文本即可。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-03.png)

### Toggle（开关）

Toggle游戏对象的文字是由其子游戏对象中的名为Label的Text（文本）游戏对象控制。选项的框和选中时候显示的勾都是Image（图像）游戏对象。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-03.png)

Toggle开关游戏对象的【Is On】属性可以设置是否选中当前选项。	默认情况下，Toggle相互没用关联，或者说，默认的时候是多选按钮。只有设置了【Group】属性，才能成为单选按钮。

将相关的几个Toggle游戏对象的【Group】属性都设置为该添加了Toggle Group组件的游戏对象。此时，相关的几个Toggle游戏对象就会变成单选按钮，即同时只能选中其中的一个

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-04.png)

### Slider（滑动条）

Slider滑动条游戏对象的外观是由3个Image（图像）游戏对象组成。其中，【Background】是没用完成部分的显示，【Fill Area】是完成部分的显示，【Handle Slider Area】是可以点击拖动的部分。把【Handle Slider Area】隐藏或者删除就可以当进度条使用。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-05.png)

Min Value（最小值）/Max Value（最大值）用于设置滚动条的值的范围，默认的值的范围是0到1的浮点数，在Unity中很多内容加载的进度都是以这个来计算的。可以根据需要设置成其他的范围，例如从0到100。默认情况下，值是浮点数，如果选中了Whole Numbers整数选项，则值会变成整数。

### Scrollbar（滚动条）

Scrollbar和Slider很像，Slider通常用于显示而Scrollbar通常用于控制。

Number Of Steps（步数）用于设置滚动条允许的不同滚动位置的数量，默认值为0。当该属性为0时，控制柄可以在滚动条内平滑滚动。当该数值大于0时，则控制柄在滚动条内就只有固定的几个位置可以停靠。

### Dropdown（下拉选单）

【Label】子游戏对象是当前选中选项的显示，【Arrow】子游戏对象是下拉图标的显示，下拉出来选择用的则是一个Scroll View滚动矩形。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-06.png)

Value（值）是当前所选选项的索引，从0开始计数。0 代表第一个选项，1 代表第二个，依此类推。Options选项列表存放下拉选单的列表，可以通过修改该属性设置下拉选单中的列表内容。

### Input Field（输入字段）

Input Field游戏对象的常用属性包括选项字符设置，类型设置，提示设置和其他设置。

Text属性可以设置和获取输入的文字内容。Character Limit属性用于设置字符数量，该属性为0则没用限制，否则输入字符数不能超过Character Limit属性值。

提示设置包括Caret Blink Rate，Caret Width，Custom Caret Color和Selection Color，用于设置插入提示符号的闪烁频率，宽度，颜色以及选中文本的背景颜色。

Read Only选中以后可以将输入字段设置为只读。

为了避免输入中文无法显示，对于其下的子游戏对象中的Text组件的Font（字体）属性最好设置为中文字体。

### Scroll View（滚动视图）

滚动视图游戏对象用于在小区域查看占用大量空间的内容。【Scrollbar Horizontal】子游戏对象是水平滚动条，【Scrollbar Vertical】子游戏对象是垂直滚动条，需要显示的内容，必须在【Content】游戏对象下。

![Unity2019常用功能:交互游戏对象](/images/20210114-Interaction-07.png)

滚动条设置包括Horizontal（水平）选项和Vertical（垂直）选项，默认都选中。取消以后，就会停止使用对应的滚动条。滚动条显示设置主要是Visibility选项，可以设置滚动条是否会自动隐藏，或者始终显示/隐藏。

> B站视频链接：[https://www.bilibili.com/video/BV1Sr4y1T7Ek/](https://www.bilibili.com/video/BV1Sr4y1T7Ek/)