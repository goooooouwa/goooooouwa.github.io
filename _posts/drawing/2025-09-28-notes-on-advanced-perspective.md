---
category: drawing
tags: perspective study-notes
published: true
title: 高级透视技巧学习笔记
---
## 复杂平面图形的透视画法

### 圆的透视画法（Projecting A Circle）

**不使用平面俯视图来构造圆形的透视（Circle Without a Plan）**

![projecting a circle without a plan.png]({{site.baseurl}}/assets/images/projecting a circle without a plan.png)

构造步骤：

1. 在画面中画出透视的正方形
1. 在透视的正方形内逐步构造出图中的辅助线
1. 根据辅助线构造出透视中的圆形

**使用平面俯视图来构造圆形的透视（Circle With a Plan）**

![projecting a circle with a plan.png]({{site.baseurl}}/assets/images/projecting a circle with a plan.png)

构造步骤：

1. 在平面俯视图中画出正方形和内嵌的圆形
1. 逐步画出辅助线
1. 将正方形和辅助线投射到画面中
1. 根据辅助线构造出透视中的圆形


### 椭圆的构造（Ellipse Construction）

每一个椭圆都可以通过它的高度和宽度来描述，这两个维度分别称为长轴（最长的方向）和短轴（与长轴垂直的方向）。由此可以得到两种简单的椭圆构造方法，以及一种估算圆在透视中缩短程度的计算方式。

**根据固定的高度和宽度来构造椭圆的3种方法**

在 **第一种方法（A）** 中，高度和宽度先定义一个矩形，然后用两条线将矩形等分为四个象限。接着，将矩形内部的一条水平线段（相当于椭圆的长轴）和矩形外部的一条垂直线段（长度等于椭圆的短轴）按同样的比例划分为相等的部分（这些点之间不必保持相等的间隔距离，只需这些点在两条线段上的比例相等即可，比如均为所在线段的4分之一长度）。然后，从中线上的两个点 a 和 b 分别向这些分点引线，如图所示。对应直线的交点定义了椭圆在一个象限中的点。最后，将这些关键点用徒手曲线或曲线板分段连接，并复制到其他三个象限中，即可得到完整椭圆。

![ellipse-construction-method-a.png]({{site.baseurl}}/assets/images/ellipse-construction-method-a.png)

另一种更高效的方法是**游标法（Trammel Method，方法 B）**。

![ellipse-construction-method-b.png]({{site.baseurl}}/assets/images/ellipse-construction-method-b.png)

具体做法是：先确定椭圆的外接矩形，然后将长轴和短轴的长度转移到一条硬纸板或厚纸条上（保持长短轴的某一端对齐，见右图）。由于长轴和短轴长度不相等，在另一端会留下一个间隔（洋红色线所示）。将这两个端点分别与椭圆矩形的短轴和长轴对齐，此时便可以直接在纸条另一端的对齐点标记出椭圆的圆周所在的位置。此方法快速，但当长轴和短轴逐渐接近相等（即椭圆趋近圆形）时，精度会显著下降。

**第三种方法（C）** 使用两个以点 a 为圆心的同心圆。

![ellipse-construction-method-c.png]({{site.baseurl}}/assets/images/ellipse-construction-method-c.png)

先画出大圆和小圆，然后用两条互相垂直的直线将其四等分，这两条直线定义了椭圆的长轴和短轴。接着，从点 a 向外任意画若干条放射线，使它们分别交小圆和大圆，得到成对的交点。然后从这些交点分别作平行于椭圆的长轴或短轴的线段；这些线的交点便是该椭圆在这个象限内所在的点。此方法的优点在于：如果将“辐射线”以及水平、垂直辅助线延伸穿过整个大圆，就能标定出完整椭圆的全部圆周。

然而，这里出现了一个问题。从下面的圆形构造图可以看出，椭圆的中心并不与图像方形的中心（即方形对角线的交点）重合，因为透视缩短导致方形的后半部分看起来比前半部分略小。因此，表示椭圆中心的黑色十字并没有位于对角线交点，而是稍微偏下（靠前）的位置。

![center of the ellipse is not coincident with the center of the image square.png]({{site.baseurl}}/assets/images/center of the ellipse is not coincident with the center of the image square.png)

这与另一个视觉差异本质相同：球体的可见圆周（等于椭圆长轴在图像中的宽度）与球体直径的视觉角度（等于透视方形中横跨中心的宽度）之间的差异（见下图）。这个问题会在下面“球体投影”章节中进一步讨论。遗憾的是，除了在平面俯视图中按比例绘制外，没有一种简单的方法能直接缩放椭圆的宽度，因为**椭圆的长轴并不与方形的中线横截线重合**，而**椭圆与方形边框相切的点通常也不位于椭圆的长轴上**。但在小于20°视角范围的透视圆中，这种误差极小，可以忽略不计。

![discrepancy between the visible circumference and angular diameter of a sphere.png]({{site.baseurl}}/assets/images/discrepancy between the visible circumference and angular diameter of a sphere.png)

这也是为什么建筑师们通常习惯使用椭圆模板以及依赖于计算机绘图软件的一个主要原因。椭圆模板包含大量切割好的椭圆，每一个都比前一个略大，并且都按照一个标准视角比例缩放，适配到包含圆的平面。绘图者只需选择与所需长短轴比例最接近的模板角度，然后再挑选最符合图像大小的椭圆切口即可。

用于估算圆的透视缩短程度（即椭圆模板角度）的方法，源自视角几何中圆内切线（trigonometric tangent）的计算：

![angle-of-view-at-x.png]({{site.baseurl}}/assets/images/angle-of-view-at-x.png)

在中轴线附近放置一个透视的正方形，从前面的一个角引出一条竖直线 A，再从斜对面的后角引出一条水平线 B；这两条线相交后形成一个直角三角形。然后用直尺测量 A 与 B 的长度，并取其比值的反正切（arctangent）。这个角度就是从点 x 处看到该方形平面的视觉角度（angle of view）。该角度可用来选择最合适的椭圆模板。

不过，建筑师们通常不会去做这些计算：他们只会**尝试不同的模板，直到在角度和尺寸上找到视觉上最接近的匹配为止**。


