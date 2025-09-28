---
title: 两点透视学习笔记
category: drawing
tags: perspective study-notes
published: true
---
两点透视的整体主题是，通过将消失点旋转特定角度以及在合适的measure bar上确定相应的measure points以便投射所需的深度等办法，确定物体在两点透视中的正确比例。

## 两点透视（Two point perspective）

### 两点透视的标志性特征（Defining Features of Two Point Perspective）

下图展示的是最简单的两点透视，一个正方体以相对画面45度角的方式摆在画面中心。

![Defining-Features-of-Two-Point-Perspective.PNG]({{site.baseurl}}/assets/images/Defining-Features-of-Two-Point-Perspective.PNG)

两点透视的物体有两个消失点（vp1和vp2），两者之间是90度。每个消失点与direction of view之间的夹角不同，但是两者之和永远是90度。沿着物体的2个消失点的方向上的深度变化是由2个测量点（mp1和mp2）来决定的。通过测量点，我们可以将measure bar或者单位长度投射到物体2个消失点所在的方向上。

## 旋转消失点（rotating the vanishing points）

![Screenshot 2024-09-14 at 11.39.24 AM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 11.39.24 AM.png)

在视觉射线法中，我们通过物体的旋转角度(angle of rotation)来定位物体的左右消失点，该角度等于物体正面与画面之间的角度，也等于物体侧面与direction of view之间的角度。通过将物体在仰视图中离观察者（viewer）最近的那个角与向上翻折的viewpoint重合，我们可以确定物体的旋转角度（angle of rotation）。接下来将物体的两边从viewpoint延长与画面相交（同时也是与地平线相交）便可以确定物体的两个消失点。

**VP定位速查表**

![vp-spacing.PNG]({{site.baseurl}}/assets/images/vp-spacing.PNG)

举例来说，假设一个正方体左侧面与direction of view的角度是30度，那么通过VP定位速查表可以得知vp1应该在地平线左侧从direction of view开始的0.58个半径长度的位置。此时正方体右侧面与direction of view的角度是60度（90-30度），对应的vp2的位置则是在地平线右侧从direction of view开始的1.73个半径长度的位置。

## 定位测量点（locating the measure points）

在一点透视中，单个消失点（principal point）决定了空间中沿着纵深线（指向principal point的消失线）方向上的透视变化，而对角消失点则可以将单位长度从图像平面映射到纵深方向上。

在两点透视中，principal point仍然定义了观察者的纵深方向的透视变化，以及direction of view在地平面和所有平行于视线方向的平面上产生的透视梯度。但物体本身的消失点却在两个不同的方向上（即两条消失线上）发生着各自的透视变化，我们的任务便是在这2条消失线上建立单位刻度。

### 测量点的几何原理（Geometry of Measure Points）

在视觉射线法中，解决这个问题的办法是将地线（ground line）上的特定长度或者单位长度映射到透视空间中物体消失点所在的方向上。

![geometry-of-measure-points.PNG]({{site.baseurl}}/assets/images/geometry-of-measure-points.PNG)

假设我们在物理空间中(注意，不是在画面中）以G为顶点GA'为半径构造出一个弧线，它与地线在A点相交。由此得到的A'GA便是一个等腰三角形，而GA'在物理空间中的长度等于GA。A'A的延长线与地平线的交点便是消失点vp1的测量点mp1。

这个构造所达到的效果是所有平行于A'A的线之间的间隔在地线（ground line）上的长度与在消失线上的长度相等。举例来讲，线条aa'和bb'是2条平行于A'A的线，这2条线在地线上的形成的线段ab的长度与物理空间中的线段a'b'是完全相等的。

### 定位测量点（Locating the Measure Points）

那么实际操作中该如何定位测量点呢？显然我们无法直接在画面上G为顶点画一条弧线，因为透视的关系，物理空间中的一条弧线会在画面中变成一个椭圆的弧线。

定位测量点其实超级简单，只需以物体的某一个消失点为顶点从向上翻折的viewpoint画一条弧线与地平线（或者说是与图像平面）相交，得到的交点便是这个消失点的测量点。这条弧线其实就是在仰视图中在viewpoint和图像平面之间构造出了一个等腰三角形。

![locating-the-measure-points.png]({{site.baseurl}}/assets/images/locating-the-measure-points.png)

因此，从 vp1 出发的圆弧与图像平面相交于 B 点；三角形 VAB 是平面仰视图中的在视点和图像平面之间的一个等腰三角形（此时相当于将其沿地平线向上翻折到90°视圈上），其底边 VB 与图像平面相交于测量点 mp1。从 vp2 出发的圆弧与图像平面相交于 Y 点；三角形 VXY 是一个等腰三角形，其底边 VY 与像平面相交于测量点 mp2。

**两点透视中如何正确地将measure bar映射到消失线上更靠前或靠后的位置**

相比于一点透视，在两点透视中使用measure bar时我们需要更加谨慎一些。在两点透视中，将measure bar放置在图形的哪一边，以及使用哪个量度点都很重要，因为此时物体的每一侧都有各自独立的量度点。

一个基本的原则是：你是在把度量单位映射到消失线（vanishing lines）上，而消失线会汇聚到一个消失点（vanishing point）。因此，你必须**使用以该消失点为顶点的圆弧所确定的对应量度点**。这个量度点位于你所要映射度量单位的那条消失线的消失点的对面一侧。

![two point perspective-projecting forward or backward from a measure bar.PNG]({{site.baseurl}}/assets/images/two point perspective-projecting forward or backward from a measure bar.PNG)

The diagram (above) shows the four possible combinations (in 2PP) for projecting from a measure bar located on either side of the anchor point. In all cases the correct measure point is the one that was defined by an arc from the vanishing point that controls the line that must be measured (as indicated by the black dot). The measure point you use is not determined by whether the measure bar is left or right of the anchor point. Note also that a point can be projected both backward and forward from a measure bar; a visual ray from the dvp verifies these forward projections.

上图展示了两点透视中将measure bar量度尺放在基准点两侧时可能出现的四种组合的情况。在所有情况下，正确的量度点总是那个由控制需要测量的消失线的消失点所画弧确定的点（图中黑点所示）。量度点的选择并不是由量度尺在基准点的左边还是右边决定的。还要注意，量度尺上的点既可以向后投射，也可以向前投射；来自距离点（dvp）的视线可以验证这些向前的投射。

If you are using a protractor centered on the viewpoint, in order to define the rotation of the vanishing points precisely, then the image plane angle is the angle between the vanishing point and a horizontal line drawn through the viewpoint (labeled x, below).

**如何使用量角器精确确定消失点的旋转角度**

如果你使用以视点为中心的量角器，来精确确定消失点的旋转角度，那么图像平面的角度就是从消失点到视点的水平线之间的夹角（在下图中标记为 x）。

![visual ray location of a measure point.PNG]({{site.baseurl}}/assets/images/visual ray location of a measure point.PNG)

Then the vanishing point for the object edge or side (vp1) will be located 90-x degrees from the direction of view (dv), and the measure point will be located x/2 degrees from the dv, on the opposite side. In the example, the front face of object BC (shown in plan) is rotated 30° to the image plane; therefore x is equal to 30°. This means vp1 will be rotated 60° away from the dv on one side, and its measure point will be located mp1 or 15° to the right. These relationships hold, no matter what orientation the object has to the image plane.

那么，物体边或侧面的消失点（vp1）将位于距视线方向（dv）90−x 度的位置，而它的量度点则位于距 dv x/2 度的位置，且在相对的一侧。举例来说，物体的正面 BC（在平面图中所示）相对于图像平面旋转了 30°；因此 x = 30°。这意味着 vp1 将在视线方向的一侧偏转 60°，而它的量度点 mp1 将位于右侧 15° 的位置。无论物体相对于图像平面如何旋转，这些对应关系始终成立。

### who has a 12 foot table?

Unfortunately it is fairly common to start with the primary form in an orientation that puts the two vp's inconveniently far apart. In the previous cube construction example, assuming a 10 foot circle of view, the cube is oriented so that the two vp's would about 11 feet apart — one 3.2 feet to the left of the dv, and the other 7.7 feet to the right. This isn't very convenient for a drafting table.

If those alternatives don't appeal to you, then you can rescale the drawing.

How do you define the crucial distance dc (from the direction of view to a vanishing point) in the first place? The easiest method is to use my [vanishing point calculator](https://www.handprint.com/HP/WCL/IMG/LPR/VPCalculator.xls) to get the measurements of the vp's and mp's, and adjust the viewing distance to the object and your angle of view until you get the proportions that seem desirable.

Or, as described above, you can reduce the circle of view to a workable size, use the method for [rotating the vanishing points](https://www.handprint.com/HP/WCL/perspect3.html#rotatingvp) to determine the locations of vp1 and vp2, measure the distance from these to dv on the diagram, then scale those distances back to life size.

Unfortunately this method, even after you get the hang of it, still forces you into a lot of poking of a pocket calculator, and is hopelessly tedious and prone to error if many lines must be inserted in your drawing. The **ultimate solution** is to generate a recession grid for the distant vanishing point, and use this grid to determine the perspective reduction for any verticals in the drawing.

![use-recession-grid-for-distant-vanishing-points.png]({{site.baseurl}}/assets/images/use-recession-grid-for-distant-vanishing-points.png)
