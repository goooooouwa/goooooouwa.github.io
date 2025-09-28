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

### 旋转消失点（rotating the vanishing points）

![Screenshot 2024-09-14 at 11.39.24 AM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 11.39.24 AM.png)

在视觉射线法中，我们通过物体的旋转角度(angle of rotation)来定位物体的左右消失点，该角度等于物体正面与画面之间的角度，也等于物体侧面与direction of view之间的角度。通过将物体在仰视图中离观察者（viewer）最近的那个角与向上翻折的viewpoint重合，我们可以确定物体的旋转角度（angle of rotation）。接下来将物体的两边从viewpoint延长与画面相交（同时也是与地平线相交）便可以确定物体的两个消失点。

**VP定位速查表**

![vp-spacing.PNG]({{site.baseurl}}/assets/images/vp-spacing.PNG)

举例来说，假设一个正方体左侧面与direction of view的角度是30度，那么通过VP定位速查表可以得知vp1应该在地平线左侧从direction of view开始的0.58个半径长度的位置。此时正方体右侧面与direction of view的角度是60度（90-30度），对应的vp2的位置则是在地平线右侧从direction of view开始的1.73个半径长度的位置。

### 定位测量点（locating the measure points）

在一点透视中，单个消失点（principal point）决定了空间中沿着纵深线（指向principal point的消失线）方向上的透视变化，而对角消失点则可以将单位长度从图像平面映射到纵深方向上。

在两点透视中，principal point仍然定义了观察者的纵深方向的透视变化，以及direction of view在地平面和所有平行于视线方向的平面上产生的透视梯度。但物体本身的消失点却在两个不同的方向上发生着各自的透视变化（即两条消失线），我们的任务便是沿着这些消失线建立单位长度。

Geometry of Measure Points. In the context of the visual ray method of perspective construction, the problem is to project a distance scale or unit dimension, defined along the ground line, into perpspective space along a vanishing line to one of the object vanishing points.

定位测量点其实超级简单，只需draw an arc from each vanishing point, from the viewpoint to the horizon line (image plane)

![locating-the-measure-points.png]({{site.baseurl}}/assets/images/locating-the-measure-points.png)


### who has a 12 foot table?

Unfortunately it is fairly common to start with the primary form in an orientation that puts the two vp's inconveniently far apart. In the previous cube construction example, assuming a 10 foot circle of view, the cube is oriented so that the two vp's would about 11 feet apart — one 3.2 feet to the left of the dv, and the other 7.7 feet to the right. This isn't very convenient for a drafting table.

If those alternatives don't appeal to you, then you can rescale the drawing.

How do you define the crucial distance dc (from the direction of view to a vanishing point) in the first place? The easiest method is to use my [vanishing point calculator](https://www.handprint.com/HP/WCL/IMG/LPR/VPCalculator.xls) to get the measurements of the vp's and mp's, and adjust the viewing distance to the object and your angle of view until you get the proportions that seem desirable.

Or, as described above, you can reduce the circle of view to a workable size, use the method for [rotating the vanishing points](https://www.handprint.com/HP/WCL/perspect3.html#rotatingvp) to determine the locations of vp1 and vp2, measure the distance from these to dv on the diagram, then scale those distances back to life size.

Unfortunately this method, even after you get the hang of it, still forces you into a lot of poking of a pocket calculator, and is hopelessly tedious and prone to error if many lines must be inserted in your drawing. The **ultimate solution** is to generate a recession grid for the distant vanishing point, and use this grid to determine the perspective reduction for any verticals in the drawing.

![use-recession-grid-for-distant-vanishing-points.png]({{site.baseurl}}/assets/images/use-recession-grid-for-distant-vanishing-points.png)
