---
title: 笔记：一点透视
category: drawing
tags: perspective study-notes
---
## 视锥框架的基本概念与名词解释

![circle-of-view-framework-basic-terms.PNG]({{site.baseurl}}/assets/images/circle-of-view-framework-basic-terms.PNG)

- image plane: 画面，即画本身所在的平面。
- ground plan: 地面。
- viewpoint: 视点，观察者眼睛所在的点，垂直于画面。
- direction of view: viewpoint与画面之间的垂线。
- principal point: direction of view与画面的交点。
- field of view: 视野，观察者眼睛的视野范围，形成了视锥的角度（degree of vision cone）。
- vision cone: 视锥，观察者在特定视野范围下（如90度视野）所能看到的实际内容，其最外围构成一个空间中的圆锥体。
- view circle: 视圈，观察者在特定视野范围下（如90度视野）所能看到的实际内容在画面上的投影，其最外围构成一个圆形。
- ground line: 地线，地面与画面相交的线。
- horizon line: 地平线，地面的消失线。
- median line：中轴线，将viewpint向上翻折后与principal point相连的线。
- plan: 地面仰视图。
- view distance: viewpoint与画面的距离。
- view height: viewpoint与地面的距离。
- vanishing point: 消失点，物体某条边在无穷远处收敛的消失点。
- diagonal vanishing point: 正方体的对角线（而不是某条边）的消失点。
- orthogonals: 纵深线，在透视中，orthogonals是指平行与direction of view的线条。


## 视觉射线法（The visual ray method）

90度视锥约定了view distance与view height相等，field of view为90度，此设定下，viewpoint经过向上翻折后，正好落在view circle上面，为透视绘画提供了很多便利。

![20230916_073333000_iOS.png]({{site.baseurl}}/assets/images/20230916_073333000_iOS.png)
![20230916_073426000_iOS.png]({{site.baseurl}}/assets/images/20230916_073426000_iOS.png)
![20240911_065745817_iOS.png]({{site.baseurl}}/assets/images/20240911_065745817_iOS.png)

### 经过双折处理后的视觉射线法（The Double Fold）——定位任何一个点在画面上的位置

视觉射线法通过将viewpoint向上翻折，同时将地面向下翻折，与画面处于同一平面，我们能够便利地**定位任何一个点在画面上的位置**。

![20240911_051309809_iOS.png]({{site.baseurl}}/assets/images/20240911_051309809_iOS.png)

只需在地面仰视图（Plan）上将物体按俯视角度确定其大小和位置，然后通过连接其在plan上的点与翻折后的viewpoint得到一条（较长的）直线，再将该点的垂直线与ground line（地线）的交点与vanishing point连接得到第2条（较短的）直线，这2条直线交叉的点即为该物体的某个点在画面中的位置。

![20240911_051404447_iOS.png]({{site.baseurl}}/assets/images/20240911_051404447_iOS.png)

![why-visual-ray-method-works.PNG]({{site.baseurl}}/assets/images/why-visual-ray-method-works.PNG)

这个基本用法只适用于物体离ground line和median line比较近的情况，如果物体离ground line（地线）和median line（中线）很远，就需要使用后面介绍的measure points和measure bar来定位了。

### 视觉射线法的应用之一（Visual Rays and Vanishing Points）——定位任意角度摆放的物体在画面中的消失点

使用视觉射线法可以轻松的**找到任意物体在画面中的消失点**。只需将地面仰视图（Plan）上的物体平移，并将任一个顶点与向上翻折后的viewpoint重合，然后沿着顶点所在的两边中的任意一条边画延长线与视平线相交，即该物体这条边所在的平面在画面中的消失点。

实际操作中，可以使用量角器测量出地面仰视图（Plan）上的物体任意一条边所在线条与direction of view（将翻折后的viewpoint与principal point相连得到的垂直线）之间的夹角，然后将量角器的中心与向上翻折后的viewpoint重合，将其0度边与direction of view重合，直接画出相等角度的线条与视平线相交，即该物体这条边所在的平面在画面中的消失点。

![Screenshot 2024-09-14 at 11.38.12 AM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 11.38.12 AM.png)
![Screenshot 2024-09-14 at 11.39.24 AM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 11.39.24 AM.png)

### 视觉射线和"透视的主要基础"（Visual Rays and the "Principal Foundation"）——

**定位物体在画面中的位置**的另一种方法是先找到物体某条边的消失点（使用上一节Visual Rays and Vanishing Points所介绍的方法），然后将仰视图中物体的这条边的延长线与ground line相交，连接消失点和ground line上的交点得到一条直线，然后将该线条在plan上的点与向上翻折后的viewpoint相连得到第2条直线（即双折法的第1条较长的构造线条），这2条直线交叉的点即为该物体这条边在画面中的位置。

该方法同样只适用于物体离ground line和median line比较近的情况。

结合以上两种方法可以看出，只要找出以下三条线中的任意两条，都可以定位物体在画面中的位置：

1. Line between viewpoint & end points. 连接 _向上翻折的viewpoint_ 与 _仰视图中物体的这条边的端点(end point)_ 所得到的直线
1. Line between vanishing point & ground line intersection. 连接 _物体某条边的消失点_ 与 _仰视图中物体的这条边的延长线与ground line的交点_ 所得到的直线
1. Orthogonals from ground line measure points. 连接 _principal point_ 与 _仰视图中物体的这条边的端点(end point)与ground line的交点_ 所得到的直线

实际操作中，当物体离ground line或median line较远时，线条1和2不易构造。

在物体离ground line较远（而距离median line比较近）的情况下，连接物体在地面仰视图（Plan）上的点与翻折后的viewpoint就变得比较困难（线条会很长），这时可以改用双折法的第2条（较短的）构造线条，即将该物体在仰视图中的一条边的两个端点(end point)的垂直线与ground line（地线）的交点与princial point(direction of view与画面的交点)连接得到的直线。此时因为物体在地面仰视图（Plan）中距离median line比较近，一个快速寻找端点(end point)垂直线与ground line（地线）的交点的方法是将ground line作为物体尺寸的测量工具（use the ground line as a ruler），根据物体在仰视图中距离median line的距离，直接在ground line上测量出交点所在的位置。

![20240911_050144353_iOS.png]({{site.baseurl}}/assets/images/20240911_050144353_iOS.png)

到这里我们会发现很重要的一点，the ground line is always the "actual size" ruler. ground line反应的是物体的实际大小。

Obviously the crucial step is still missing: how do we work with objects that are very far from the median line and/or ground line? These create ground line measure points and/or intersection points that cannot conveniently be located on the perspective drawing ground line. This challenge requires the artist to reduce the scale of the ground line ruler as a substitute for working with unreasonably large dimensions in actual size. This reduced ruler is called a measure bar, and its use is explained below.

最后一个关键问题是，当物体离ground line和median line都比较远的时候，以上的构造方法就不实用了。这时我们就需要用到measure bar，即一种缩小scale后的ground line ruler（后文会介绍具体使用方法）。

## 一点透视（One point perspective）

### 对角线和单位深度（Diagonals and the Unit Depth）

**通过单位垂直线条得到单位深度**

通过连接单位垂直线条的上端点与视锥下方的dvp（或者下端点与视锥上方的dvp）得到一条直线（即一条对角线），然后连接单位线条的另一个端点与principal point（像主点）得到第2条直线，两条线相交的点x与单位垂直线条的下端点连线与单位长度相等，即为单位深度。

![20240913_062733556_iOS.png]({{site.baseurl}}/assets/images/20240913_062733556_iOS.png)

**通过单位水平线条得到单位深度**

同样的，对于单位水平线条，可以通过连接其左端点与视锥右侧的dvp（或者右端点与视锥左侧的dvp）得到一条类似的直线（对角线），然后连接单位线条的另一个端点与principal point（像主点）得到第2条直线，两条线相交的点与单位垂直线条的连线与单位长度相等，同样可以得到单位深度。

![20240913_063754118_iOS.png]({{site.baseurl}}/assets/images/20240913_063754118_iOS.png)

### 不相等的深度间距（Unequal Spacing in Depth）

借助measure bar我们可以在画面中将任意长度转换为对应的深度，不用只局限于单位长度。

具体的步骤是：

1. 画一条水平条线；
1. 在水平条线上标记你像画的任意长度；
1. 连接measure bar上的任一measure point与对立的左侧（或者右侧）的dvp得到一条直线；
1. 连接measure bar的0刻度的点与vanishing point得到第2条直线；
1. 两条直线的交点即为该measure point对应长度在画面中的深度。

![Screenshot 2024-09-14 at 11.49.15 AM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 11.49.15 AM.png)

Diagonal lines from each point to the mp **transfer these measures into perspective depth** at the points where the lines intersect the vanishing line.

### 单位水平或垂直线段可以任意旋转或平移（Shifting the Unit Dimension）

单位水平或垂直长度线段可以在画面中同一透视深度上任意的旋转（rotate）或平移，移动后其长度不变。

![perspec3q.gif]({{site.baseurl}}/assets/images/perspec3q.gif)

### 单位深度线段无法旋转或平移（Unit depth dimensions may not be shifted or rotated）

但是单位深度无法自由地反转（rotate）或平移，因为不同位置深度会因为透视而有所不同。

## 倾斜面和坡斜面（slanting & sloping planes）

画倾斜面的方法很简单，只需将纸张以同样角度旋转，让倾斜面看起来水平即可当作普通水平面处理。

![20240911_055615053_iOS.png]({{site.baseurl}}/assets/images/20240911_055615053_iOS.png)

画坡斜面的办法是，将viewpoint向视锥左（或右）侧翻折（与dvp重合），然后在dvp画一个与坡斜面相同的角度，其中一条线与视平线重合，另一条线与median line的交点即该坡斜面的slope vanishing point（斜坡消失点）。找到斜坡消失点，剩下的就很简单了。

![20240911_060337731_iOS.png]({{site.baseurl}}/assets/images/20240911_060337731_iOS.png)

## 距离和大小（distance & size）

![20240911_061325138_iOS.png]({{site.baseurl}}/assets/images/20240911_061325138_iOS.png)

## 缩放画面（scaling the drawing）

缩放的具体步骤是：

1. 根据设想的view distance，view height，结合ground line来画出单位长度的实际大小（比如1米）；
1. 通过缩放（scaling）将实际的大小缩放相应的倍数（比如缩小10倍），令其完整的出现在所选择的format（画材）的画面中，此时我们就得到了一个单位长度在画面中特定透视深度的大小（具体深度距离可以通过scale的倍数算出来）；
1. 接下来我们就可以以画面中的该单位长度为参考，相应的画出其他尺寸的物体。

![Screenshot 2024-09-14 at 12.04.54 PM.png]({{site.baseurl}}/assets/images/Screenshot 2024-09-14 at 12.04.54 PM.png)

## 构造一个1点透视的立方体（constructing a 1PP cube）

构造1点透视的具体步骤是：

1. 确定画面中的anchor point和anchor line；
1. 根据anchor point和anchor line画出立方体的正面（如果是长方形则需要根据其实际长宽比来画）；
1. 将立方体的四个顶点与vanishing point相连；
1. 如果该立方体是正方体，则只需将立方体的四个顶点与对应方向的dvp相连，每条直线分别与上面四条直线的交点即为正方体在画面中的另外4个顶点；
1. 如果是深度与长度或宽度不相等的立方体，则可以通过利用measure bar将相同的长度或宽度映射成对应的深度。

至此得到1点透视画面中的立方体。

![constructing-1pp-cube.png]({{site.baseurl}}/assets/images/constructing-1pp-cube.png)
