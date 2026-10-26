---
title: 笔记：三点透视
category: drawing
tags: perspective study-notes
published: true
---
* TOC
{:toc}

原文地址：[https://handprint.com/HP/WCL/perspect4.html](https://handprint.com/HP/WCL/perspect4.html)

系列笔记：

1. [笔记：现实中的透视]({% post_url drawing/2025-10-16-notes-on-perspective-in-the-world %})
1. [笔记：一点透视]({% post_url drawing/2024-09-13-notes-on-central-perspective %})
1. [笔记：两点透视]({% post_url drawing/2025-09-26-notes-on-2-point-perspective %})
1. [笔记：三点透视]({% post_url drawing/2026-10-25-notes-on-3-point-perspective %})
1. [笔记：高级透视技巧]({% post_url drawing/2025-09-28-notes-on-advanced-perspective %})

## 三点透视（three point perspective）

两点透视的核心几何模型是向上翻折的视点，而三点透视更复杂一点，使用的是透视金字塔。两点透视可以通过向上翻折的视点轻松地将物体旋转任意角度，而三点透视每次旋转物体角度需要重新定位三个消失点。

两点透视的视域圆几何设置： 在“视觉光线法”（Visual Ray Method）中，将视点（Viewpoint）折叠放置于90度**视域圆（Circle of View）**的最顶端，向下俯视地平线。

理解三点透视的核心几何模型：**透视金字塔**。

三点透视中的三个消失点（vp1, vp2, vp3）在三维空间中代表三个相互垂直的光线方向。把视点（Viewpoint）看作金字塔的顶点，三个消失点看作基底，就构成了一个高为观察距离（即90度视域圆半径）的三棱锥。将物体在空间中旋转任意角度，就是将这个三棱锥在视线周围进行倾斜（俯仰角）与旋转（偏航角）。

![three-point-perspective.PNG]({{site.baseurl}}/assets/images/three-point-perspective.PNG)

## 透视草图构造法（the perspective sketch construction method）

该方法基本思路是先画出物体的大致形状，这样就能找到消失点和测量点。然后利用这些点，以精确的透视效果重建物体的基本形状，并在同一透视空间内围绕基本形状添加其他物体。这种方法适合知道所要绘制物体的大致方位，但不确定透视消失点的情况。

如何根据物体找到三点透视的90度视锥

1. 先跟据立方体的边找到3个消失点
2. 分别通过每个消失点朝另外2个消失点连线作3条垂线
3. 3条垂线的交点即视点dv
4. 以任意2个消失点的连线（比如vp2和vp3）为直径做半圆，即泰勒斯半圆
5. 延长另一个消失点（vp1）的垂线与泰勒斯半圆相交于C点，垂线与vp2和vp3连线相交于P点
6. 以P为圆心，PC为半径画圆
7. 沿dv画一条平行于vp2和vp3连线的平行线
8. 平行线与PC为半径的圆的交点H1（或H2）与dv的连线即为90度视锥的半径。

![three-point-perspective-the-vanishing-line-triangle.PNG]({{site.baseurl}}/assets/images/three-point-perspective-the-vanishing-line-triangle.PNG)

![three-point-perspective-constructing-the-auxiliary-horizon-lines.PNG]({{site.baseurl}}/assets/images/three-point-perspective-constructing-the-auxiliary-horizon-lines.PNG)

![three-point-perspective-constructing-the-circle-of-view.PNG]({{site.baseurl}}/assets/images/three-point-perspective-constructing-the-circle-of-view.PNG)

![Anotated illustration]({{site.baseurl}}/assets/images/d6f72063dfaa4c8396221ae53e3aace4.jpg)

**如何只用圆规（不用量角器和直尺）画出3条垂直于消失线的辅助消失线**

在这个例子中，我们是从vp2出发，作垂直于对面消失线。所以属于[此文](https://handprint.com/HP/WCL/construct.html)中提到的下面这种情况：

> What if you have to start with a point off the existing line, such as NP? No sweat: first draw a circle with NP as its center so that it crosses the existing line at two points, A1 and A2. Then proceed with steps 2 and 3, as before.  

具体步骤如下：
1. 以vp2为圆心、vp2和vp3的连线为半径画圆，与vp1和vp3的连线相交于Y点（vp3和Y点即是前文中所谓的A1和A2）；
2. 然后以Y为圆心、画一个任意半径（只要大于Y和vp3连线的一半）的圆；
3. 再以vp3为圆心，画一个同样半径大小的圆
4. 两个圆相交的点之一即为P2；
5. 将vp2与P2连线即得到一条经过vp2且垂直于vp1和vp3连线的线条。

![Anotated illustration]({{site.baseurl}}/assets/images/d02faafb29394de982fa5c940d47a944.jpg)

**泰勒斯半圆（Semicircle of Thales）**

泰勒斯半圆（Semicircle of Thales）就是以 vp1 与 vp2两点连线为直径所绘制的半圆。

![Anotated illustration]({{site.baseurl}}/assets/images/41ee6af7e3f140cd864123adfa7c9d07.jpg)
