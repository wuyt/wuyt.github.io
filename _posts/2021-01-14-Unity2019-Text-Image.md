---
layout: post
title: Unity2019常用功能:文本和图像
date: 2021-1-14 11:00:05 UTC+8
tags: [Unity,Learn,Text,Image,Unity UI]
category: [Software]
description: Unity,Learn
---

文本和图像组件在官方文档中被称为Visual Components可视组件，是其他一些被称为Interaction Components交互组件基础。交互组件的外观都是由文本和图像组件构成的，Interaction Components交互组件的外观调整都是基于Visual Components可视组件。

<!-- more -->

### Text（文本）游戏对象

Character（字符）属性中包括了Font（字体），Font Style(字体样式)等。中文内容在某些机型上会出现乱码或无法显示的情况，所以，用到中文最好还是设置字体，本人经常使用的是思源黑体，8M左右。

Best Fit（自适应）选中以后，可以设置显示的最小字体和最大字体，系统将根据文字内容的多少自动设置字体大小，在处理不同大小屏幕的时候经常用到。

Unity还提供了字体轮廓和阴影的组件，可以设置字体的阴影和轮廓。

对于初学者的，不建议在富文本，边框，阴影和材质上花太多精力，如果需要将文本变得很漂亮，请考虑使用TextMesh Pro。

### Image（图像）游戏对象

Unity有2种图像相关的游戏对象，Image（图像）游戏对象和Raw Image（原始图像）游戏对象。Raw Image游戏对象的优点是可以设置任何纹理图片用于显示，Image游戏对象则只能使用Sprite（精灵）的图片纹理用于显示，但是Image游戏对象在对齐方面有优势。通常，UI还是推荐使用Image游戏对象，只有在需要显示动态内容如视频，3D模型，物理摄像头内容的时候才考虑用Raw Image游戏对象。

导入的图像文件默认【Texture Type（纹理类型）】为“Default”，在【Project（项目窗口）】选中图像资源以后，在【Inspector（检查器窗口）】，选择【Texture Type】的属性为“Sprite(2D and UI)”，然后点击【Apply】按钮，即可将纹理类型设置为Sprite精灵类型。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-01.png)

Image图像游戏对象有4种图像展示类型。

简单类型是最基本的展示方法，将【Image Type】的值设置为“Simple”，此时，可以通过选中【Preserve Aspect】选项保持图像的长宽比例，也可以通过点击【Set Native Size】将图像大小设置为与图像分辨率一致。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-02.png)

平铺模式通常用于比较小的图像，通过循环显示的方式来显示成一个大的图像。将【Image Type】的值设置为“Tiled”之后，图像会重复铺满整个显示区域。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-03.png)

将【Image Type】的值设置为“Filled”则进入填充模式，该模式下，图像会以不同的方式填充在显示区域内。这种模式更多的是用于动态展示图像出现的过程。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-04.png)

九宫格显示主要是用于背景或者按钮等类型的显示，只用一个图像纹理，就能适应多种大小和长宽比的显示，并且保持风格一致。

首先需要安装“2D Sprite”插件。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-05.png)

安装好以后，点击【Sprite Editor】按钮，则会弹出【Sprite Editor】窗口。此时在图像的4个边上有4条线。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-06.png)

将4条线拖到图像中，利用4条线将图像分割为9个部分。点击【Apply】按钮即可。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-07.png)

这里，9个部分中，中心的区域是被上下左右拉伸填充的，上下和左右的区域只被水平和垂直拉伸，4个角的图像不会变。	此时将这个图像纹理设置为Image图像游戏对象的【Source Image】属性的值，将【Image Type】设置为“Sliced”切片。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-08.png)

### Raycast Target（光线透视目标）选项

Raycast Target光线透视目标选项默认为选中状态，此时点击只会影响到最上层的UI。如下图中，当一个Image图像覆盖住一个Button按钮的时候，此时是无法点击到按钮的。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-09.png)

如果取消Image图像游戏对象的Raycast Target光线透视目标选项，则可以点击下方的按钮。这个在设计某些复杂的UI的时候会需要用到。

### Mask（遮罩）和Rect Mask 2D（矩形遮罩）

Mask遮罩组件Mask遮罩和Rect Mask 2D遮罩组件都是用于限制子游戏对象的显示范围和形状。可以通过父游戏对象（Text文本游戏对象或者Image图像游戏对象）内容形状实现特定形状的显示。

Rect Mask 2D遮罩组件只能显示显示为矩形，但是性能更高，使用也更方便，如果只是显示矩形区域，推荐使用Rect Mask 2D遮罩组件。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-10.png)

Mask遮罩组件需要有Image图像游戏对象或者Text文本游戏对象作为模板，不可以建立在空的游戏对象上。如果Mask遮罩组件所在的Image图像游戏对象的图像是渐变图像，则显示的内容也会有渐变效果。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-11.png)

如果用Text文本游戏对象代替Image图像游戏对象，则效果如下。

![Unity2019常用功能:文本和图像](/images/20210114-Text-Image-12.png)

> B站视频链接：[https://www.bilibili.com/video/BV1So4y1d7ZS/](https://www.bilibili.com/video/BV1So4y1d7ZS/)

> B站视频链接：[https://www.bilibili.com/video/BV1bh411y7R5/](https://www.bilibili.com/video/BV1bh411y7R5/)