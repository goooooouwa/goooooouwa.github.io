---
title: 如何根据画面判断镜头的视距、视高和俯仰角度
category: drawing
tags: perspective
published: true
---
* TOC
{:toc}

[透视系列笔记]({{ site.baseurl }}/tag/perspective)

## 基本概念

### 画的本质

一幅画的本质是一种视错觉，它试图模仿的是当一位观察者站在特定的视高和视距下，视线垂直于图像平面时，透过图像所在的画框（这个透明的窗户）所看到的三维空间的样子。

### 共同的前提和假设

每一副画作都有一些共同的前提和假设：
1. 观察者眼睛所看到的90度视锥的半径等于观察者的视距（这是基本数学原理）；
2. 为了避免画面出现明显的透视扭曲 (perspective distortion) ，图像画面通常会被安排在60度视锥之内；
3. 观察者的视线永远是垂直于图像平面的（画框可以相对于地面有各种不同的俯仰角度）；

### 视距

作者可以通过选择不同的视距来控制90度视锥所能看到的三维空间的范围，更长的视距意味着观众通过同样尺寸的画框所能看到的三维空间更小，因为画面的视觉角度更窄。

### 视高

作者可以为画面选择选择不同的视高，以营造出不同身高的观察者或者观察者视线处在不同水平高度（比如匍匐在地面或者站在楼顶）时透过画框所看到的三维空间的样子。

![horizon line and viewpoint in landscape perspective.PNG]({{site.baseurl}}/assets/images/horizon line and viewpoint in landscape perspective.PNG)

### 俯仰角度

画框这个透明的窗户可以相对于地面有各种不同的俯仰角度，但观察者的视线永远是垂直于图像平面的（否则为了真正欣赏一副作品，观众就必须先找到作家设定的特定的观察角度，会很麻烦）。

如果镜头相对地面产生俯仰角度，画面中的垂直方向便会新增一个消失点（天空中或者地底下），这时原本是一点透视的画面会变成垂直方向的两点透视，而两点透视的画面则会成为三点透视。因此一个快速判断镜头是否相对于地面有俯仰角度的办法是，检查垂直于地面的物体（比如建筑物）是否出现透视现象（寻找消失点，即多条垂直于地面的线条之间的交点）。

![looking downward.PNG]({{site.baseurl}}/assets/images/looking downward.PNG)

如果镜头相对地面存在俯仰角度，则可以通过测量地平线与视平线在dvp处的夹角来确定画面的**俯仰角度**（参考[倾斜面和坡斜面]({% post_url drawing/2024-09-13-notes-on-central-perspective %})一节）。

## 确定画面的关键透视点

### 如何根据画面内容确定一点透视的关键点（中央消失点和视距等）

![1PP reconstruction of the center of projection.PNG]({{site.baseurl}}/assets/images/1PP reconstruction of the center of projection.PNG)

1. 根据画面中的纵深线（orthogonals，即垂直于画面的线条）确定中央消失点；
2. 根据中央消失点和画面中地面上的元素确定地平线（通常等于视平线）以及median line的位置；
4. 根据画面中的对角线（diagonals，与median line之间夹角45度的线条，比如地面上平行于ground line的正方形瓷砖的对角线）确定dvp（对角线消失点）；
5. 找到了dvp也就顺便确定了view distance（视距）；
6. 有了view distance（视距）和中央消失点，便可以确定90度和60度视锥的大小。

至此一点透视的关键点就都确定了下来。

### 如何根据画面内容确定两点透视的关键点（消失点和direction of view等）

![2PP reconstruction of the center of projection.PNG]({{site.baseurl}}/assets/images/2PP reconstruction of the center of projection.PNG)

1. 根据画面中的直角线条确定两个vanishing points；
2. 将2个vanishing points连线即可得到视平线（通常等于视平线）；
3. 根据画面中的纵深线（orthogonals，即垂直于画面的线条）找到direction of view并确定median line的位置；
4. 在median line上找到一个点，它与两个vanishing points的连线正好是90度，而这个点便是向上翻折后的视点（folded viewpoint）；
5. 找到了folded viewpoint也就顺便确定了view distance（视距）和principal point（观察者眼睛的位置）；
6. 有了view distance（视距）和principal point，便可以确定90度和60度视锥的大小。

至此两点透视的关键点就都确定了下来。

#### 如何确定median line

**Median Line.** This is parallel to the side edges of a rectangular image format, or perpendicular to the floor when the painting is correctly hung. **The median line is nearly always through the center of the image format.**

如果可以在画面中找到纵深线（orthogonals，即垂直于画面的线条），则可以根据纵深线与地平线的交点确定direction of view，进而确定median line的位置；如果画面中没有明显的垂直于画面的线条（即纵深线，Orthogonals），则可以将垂直平分画面的竖线作为median line，因为median line几乎总是穿过画面中心的（画家通常都会将center of view设置于画面的垂直中心线上，因为观察者在欣赏画作时会很自然地站在画面的正前方）。
 
> Orthogonals, if visible, will point to the direction of view on the horizon line; if there are no orthogonals, then the median line of the format can be used to locate the dv.
> 
> (if there are no orthogonals) The median line and direction of view (dv) are arbitrarily located on the midline of the painting.

### 实战演练

![perspective analysis.jpg]({{site.baseurl}}/assets/images/perspective analysis.jpg)


## 如何根据画面判断镜头的视距、视高和俯仰角度

1. 先确定画面的关键透视点（消失点、地平线、center of view等）；
2. 找到（一点透视的）dvp或者（两点透视的）folded viewpoint后便确定了**视距**；
3. 画面中任何处于地平线上的物体（比如人的头部、树的枝干或者建筑物的墙壁），其距离地面的垂直距离等于观察者眼睛与地面的距离（即**视高**），然后可以根据[距离和大小]({% post_url drawing/2024-09-13-notes-on-central-perspective %})来推算出实际的视高；
4. 检查垂直于地面的物体（比如建筑物）是否出现透视现象（即是否存在垂直方向的消失点），如果存在，则可以根据地平线与视平线在dvp处的夹角确定画面的**俯仰角度**（参考[倾斜面和坡斜面]({% post_url drawing/2024-09-13-notes-on-central-perspective %})一节）；

### 根据视距、物体画面大小和实际大小确定物体与观察者的实际距离

![reduction in Bierstadts Looking Up the Yosemite Valley.PNG]({{site.baseurl}}/assets/images/reduction in Bierstadts Looking Up the Yosemite Valley.PNG)

如果已知观察者的视距（比如根据画幅的尺寸或者展览馆里作品的摆放来推测理想的欣赏距离，即为视距），且已知物体画面大小（直接在画面上测量）和物体的实际大小（根据现实生活中可以查到的物体数据），根据[距离和大小]({% post_url drawing/2024-09-13-notes-on-central-perspective %})，我们可以计算出物体在三维空间中与画家（或者说假象的观察者）的实际距离。

## 参考

- [https://handprint.com/HP/WCL/perspect2.html](https://handprint.com/HP/WCL/perspect2.html)
- [https://handprint.com/HP/WCL/perspect3.html](https://handprint.com/HP/WCL/perspect3.html)
