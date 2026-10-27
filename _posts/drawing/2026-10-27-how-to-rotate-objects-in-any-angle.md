---
title: 总结：如何在透视画面中画任意角度、任意大小的物体
category: drawing
tags: perspective
published: true
---

[透视系列笔记]({{ site.baseurl }}/tag/perspective)

* TOC
{:toc}

## 透视画法的第一步：建立透视网格

2点透视可以在地面上画一些透视线构成平面透视网格，如果是3点以上的透视图，除了地面上的平面透视图，还可以在空间中画一些透视线，体现出每个透视消失点对应线条的收缩变化。**只要有了这些透视辅助线，其实也可以不用把消失点画出来**。对于透视消失点距离很远的构图，可以使用下面的Brewer Method构建透视网格。

## Brewer Method: 如何绘制消失点距离很远的物体（How to draw with vanishing points off the paper）

在画透视时，有时消失点因为距离太远，无法在纸上标记，这时可以用Brewer Method。

1. 首先在草稿上画一个微缩版的透视图，确定所有消失点的位置，根据消失点确定所画物体3条边（地面上的2条底边和其中1个侧面的顶边）的角度（确定角度是关键，虽然放大后物体的尺寸会发生变化，但同一段线条的透视角度会保持不变）；
2. 在纸上进行正常尺寸的绘画，将微缩版的物体2条底边角度平移到纸上，根据画面尺寸随意选定第3条线（即那条侧面的顶边）的高度（这个高度只影响画面的大小尺寸，不影响透视关系）；
3. 在3条线内画一个矩形，其3个角正好跟3条边接触，由此可以确定第4条边的角度（不过好像也可以直接从微缩图中平移第4条线段，所以brewer method不是必须的）；
4. 在确定了物体的4条边的方向后，便可以对垂直方向的3条边进行不断地二分，得到局部的透视网格；
5. 基于局部的透视网格进行作画。

![brewer-method.png]({{site.baseurl}}/assets/images/brewer-method.png)

## 如何将正方体在2点透视中旋转任意角度

1. 首先建立2点透视（视锥，水平线，2个消失点）
2. 在地面画一个立方体
3. 在立方体内部画一个圆（参考how to draw with imagnation这本书里的怎么画圆）
4. 选定任意新的物体旋转角度（在水平线上确定2个新的消失点）
5. 从2个消失点分别画2条线正好与圆相切，得到一个新的正方形，这个正方形与之前的立方体底面大小相当
6. 根据旋转后的正方形画出该角度下的立方体

![drawing-spider-using-armature-projection.PNG]({{site.baseurl}}/assets/images/roate-objects-in-any-angle.png)

对于复杂图形，可以先画出物体所在的正方体，并且在正方体的底面和侧面将物体的投影进行标记，然后在旋转后的新立方体中找到物体的投影所在位置，重新勾勒出该物体的立体图形。

![drawing-spider-using-armature-projection.PNG]({{site.baseurl}}/assets/images/drawing-spider-using-armature-projection.PNG)

## 如何在透视画面中画任意远近的物体

先确定单位长度（比如以人的头部为单位），再将其旋转到任意方向上，然后沿着透视方向移动（相应地放大或缩小）。

