---
title: 如何根据画面判断透视类型以及视距、视高和俯仰角度
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

根据透视的平移缩放规则可知，画面的视高是可以任意设定的，不用一定等于视距（比如当观察者趴在地上或者站在高楼上）。90度视锥假设视高等于视距只是为了方便根据90度视锥建立ground line以及定位翻折后的视点（viewpoint）。实际作画中可以任意选择视高和视距，只要画面不要超出60度视锥即可。

作者可以为画面选择选择不同的视高，以营造出不同身高的观察者或者观察者视线处在不同水平高度（比如匍匐在地面或者站在楼顶）时透过画框所看到的三维空间的样子。

![horizon line and viewpoint in landscape perspective.PNG]({{site.baseurl}}/assets/images/horizon line and viewpoint in landscape perspective.PNG)

### 俯仰角度

画框这个透明的窗户可以相对于地面有各种不同的俯仰角度，但观察者的视线永远是垂直于图像平面的（否则为了真正欣赏一副作品，观众就必须先找到作家设定的特定的观察角度，会很麻烦）。

如果镜头相对地面产生俯仰角度，画面垂直方向便会新增一个消失点（天空中或者地底下），这时原本是一点透视的画面会变成垂直方向的两点透视，而两点透视的画面则会成为三点透视。因此一个快速判断镜头是否相对于地面有俯仰角度的办法是，检查垂直于地面的物体（比如建筑物）是否出现透视现象（寻找消失点，即多条垂直于地面的线条之间的交点）。

调整俯仰角度会在画面垂直方向新增一个消失点：

![looking downward.PNG]({{site.baseurl}}/assets/images/looking downward.PNG)

如果镜头相对地面存在俯仰角度，则可以通过测量地平线与视平线在dvp处的夹角来确定画面的**俯仰角度**（参考[倾斜面和坡斜面]({% post_url drawing/2024-09-13-notes-on-central-perspective %})一节）。

#### 调整视高与调整俯仰角度对画面透视产生的影响

![change-view-height-vs-view-angle.png]({{site.baseurl}}/assets/images/change-view-height-vs-view-angle.png)

对比初始画面（图一）与低视高画面（图二）可以得出，在视线角度保持不变的情况下将视点进行任意的上下左右平移后，画面的透视特征将保持不变（包括center of view，视平线、地平线和消失点的位置等），画面中同一个物体的所有平行于画面的平面大小都将保持不变。（参考平移透视缩短）。

对比初始画面（图一）与俯视画面（图三）可以得出，如果镜头相对地面产生俯仰角度，画面垂直方向便会新增一个消失点（天空中或者地底下），这时原本是一点透视的画面会变成垂直方向的两点透视，而两点透视的画面则会成为三点透视。

![change-view-height-vs-view-angle-continued.png]({{site.baseurl}}/assets/images/change-view-height-vs-view-angle-continued.png)

对比高视高画面（图一）与俯视画面（图二）可以得出，当视线角度发生变化后，画面中的同一个物体最多只会有一条边可以在画面中保持大小位置不变，其他部位的大小和位置都会发生变化。

![2025-10-16 perspective analysis_ difference between changing view height and changing view angle.png]({{site.baseurl}}/assets/images/2025-10-16 perspective analysis_ difference between changing view height and changing view angle.png)

对比高视高画面（图一）与俯视画面（图二）可以得出，当视线角度发生变化后，即使同一个物体在画面的水平方向高度保持不变，其他部位的大小和位置依然会发生变化（比如物体的宽度会变，物体侧边线条的角度也会发生变化。整个画面都展现出同样的变化。

#### 仰视角度与俯仰角度对画面透视产生的影响

![changing view angle.png]({{site.baseurl}}/assets/images/changing view angle.png)

对比仰视画面（图三）与俯视画面（图二）可以得出，无论视线角度怎么改变，低于视平线（即视高）的物体其顶部（在不被其他物体遮挡的情况下）永远都是可见的，反过来高于视平线（或视高）的物体其底部同样也是永远可见的。

比如在下图中，观察者的视高高于篮球员的右脚，由此可知，无论观察者以多少角度仰视或者俯仰该篮球员，观察者永远都只能看到篮球员右脚的顶部，不可能看到其脚底（除非将视高降到右脚以下）。

![view-angle-view-height]({{site.baseurl}}/assets/images/view-angle-view-height.png)

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
 
> Orthogonals, if visible, will point to the direction of view on the horizon line; if there are no orthogonals, then the median line of the format can be used to locate the dv.
> 
> (if there are no orthogonals) The median line and direction of view (dv) are arbitrarily located on the midline of the painting.

**如果可以在画面中找到纵深线（orthogonals，即垂直于画面的线条），则可以根据纵深线与地平线的交点确定direction of view，进而确定median line的位置**；如果画面中没有明显的垂直于画面的线条（即纵深线，Orthogonals），则可以将垂直平分画面的竖线作为median line，因为median line几乎总是穿过画面中心的（画家通常都会将center of view设置于画面的垂直中心线上，因为观察者在欣赏画作时会很自然地站在画面的正前方）。

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

### 根据物体画面大小和实际大小确定视距

例如，观察者站在一个身高为1.8米的人面前，沿水平方向直视对方，测量得知此人的头部在画面中的身高是18厘米，而90度视锥半径的测量长度是20厘米，求观察者与画面之间的距离（即视距）。

1. 画一幅画面的草图，此时不用考虑透视问题（比如，视距，视高，视锥角度等）；
2. 在画面外围画一个圆，将画面包围起来，以这个圆为60度视锥（也可以是25-60度之间的任意角度，这样可以保证画面内不会出现夸张的透视形变），在画面中心作一条垂直线作为median line；
3. 在60度视锥外围画一个90度视锥（与60度视锥同心，半径是60度视锥的1.72倍，即1 / 0.58）；
4. 根据90度视锥框架的几何属性可知，90度视锥的半径即等于视距；
5. 在90度视锥下方画一条平行于地平线的水平线，即ground line（如果找不到地平线，也可以在90度视锥下方画一条水平线，因为它与ground line同样处在画面所在的平面中，所以可以作为一条与ground line等比例的参考线条）；
6. 将画面中已知尺寸的物体根据透视规则移动到ground line上（并进行相应的缩放），测量出它在ground line上的实际尺寸，即可根据画面和物体大小比例关系计算出画面的视距长度（比如，已知一个人的头部高度是20厘米，将画面中此人的头部移动缩放到ground line后，假设测量出其头部的实际尺寸为10厘米，那么可知整幅画面相比与理论尺寸缩小了2倍，而假如测量出的视距大小为20厘米，那么画面的实际视距即为40厘米）；
7. 至此，便可将任意其他物体的实际尺寸按照画面缩放倍数在ground line上画出同等长度的线段，然后根据透视规则，将其移动缩放到画面空间中的任意位置。

### 根据物体实际大小和视距确定其在画面中的位置和大小

例如，已知观察者坐在长度为1米的方形桌子前，以45度角俯视桌子，此时画面中可以看到整个桌子，观察者的视线（direction of view）正好穿过桌子表面的1/2处，要求画出当画面距离观察者视距为80厘米时，桌子在60度视锥中的画面的位置和大小。

确定物体的上下轮廓在画面中出现的位置和大小：

1. 根据画面要求推导出画面的侧视图（包括观察者的位置和视线方向）；
2. 依次在侧视图中画出90度视锥（即两条被视线平分的夹角为90度的线）和60度视锥；
3. 根据侧视图中物体的画面大小和实际大小得出画面的缩放比例（比如，在侧视图中测量得出桌子表面的长度是10厘米，而已知桌子的长度是1米，可知侧视图的缩放比例是1/10）；
4. 根据视距和缩放比例可以得知侧视图中视距的画面大小，进而确定画面平面所在的位置（比如，已知视距为80厘米，缩放比例是1/10，那么侧视图中视距的画面长度即为8厘米，进而可以从观察者沿着视线方向画一条8厘米的线段，在线段的另一端画一条垂直于视线方向的线条，该线条于60度视锥的两个交点分别对应画面的上下边缘）；
5. 在侧视图中将物体上的任意点与视点连接后，其与画面的交点即为该点在画面中的位置，可以据此确定物体的上下轮廓在画面中出现的位置（比如根据连线可以确定桌子表面上下边缘分别出现在画面中的位置）；
 
确定物体的左右轮廓在画面中出现的位置和大小：

1. 根据画面要求推导出画面的俯视图（包括观察者的位置和视线方向）；
2. 依次在侧视图中画出90度视锥（即两条被视线平分的夹角为90度的线）和60度视锥；
3. 根据同样的办法（即画面的缩放比例）确定视距在俯视图的画面大小，进而确定画面平面的位置；
4. 在俯视图中将物体上的任意点与视点连接后，其与画面的交点即为该点在画面中的位置，可以据此确定物体的左右轮廓在画面中出现的位置（比如根据连线可以确定桌子表面左右边缘分别出现在画面中的位置）。

## 参考

- [https://handprint.com/HP/WCL/perspect2.html](https://handprint.com/HP/WCL/perspect2.html)
- [https://handprint.com/HP/WCL/perspect3.html](https://handprint.com/HP/WCL/perspect3.html)
