---
layout: default
title: 如何用Construct2制作猎人打鸟小游戏
---

#如何用Construct2制作猎人打鸟小游戏

##前期准备工作

前往https://www.scirra.com/construct2 下载并安装construct2

##开始制作

打开construct2,如图操作。
![2-1](images/2-1.jpg)

1、选取背景图片（例如下图）进行平铺
![bg](images/bg.png)
在layout中双击白色背景，在弹窗中选择Tiled Background > Insert
十字图标点击中间附近的位置，在弹窗中选择load an image from a file,选择之前下载好的背景图片，窗口中便会显示之前下载的图片，之后点窗口右上角的X退出纹理编辑器，会发现背景图片已经出现在屏幕中间了。接下来，我们在左侧的参数栏中调整position为0，0，size为1280，1024。
![2-2](images/2-2.jpg)

2、添加图层

在右侧栏中选择“layers”，点击铅笔图标，将0图层名称改为Background。点击锁图标，锁定图层以防更改。点击加号，添加图层命名为“Main”。

3、添加对象

选中Main图层，双击插入新对象。这次选择“Mouse”。同样操作添加“Keyboard”。接下来，我们添加游戏对象。

玩家:![player](images/player.png)

怪兽:![monster](images/monster.png)

子弹:![bullet](images/bullet.png)

特效:![explode](images/explode.png)