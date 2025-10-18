---
title: 笔记：现实中的透视
category: drawing
tags: perspective
published: true
---
* TOC
{:toc}

原文地址：[https://handprint.com/HP/WCL/perspect1.html](https://handprint.com/HP/WCL/perspect1.html)

系列笔记：

1. [笔记：现实中的透视]({% post_url drawing/2025-10-16-notes-on-perspective-in-the-world %})
1. [笔记：一点透视]({% post_url drawing/2024-09-13-notes-on-central-perspective %})
1. [笔记：两点透视]({% post_url drawing/2025-09-26-notes-on-2-point-perspective %})
1. [笔记：高级透视技巧]({% post_url drawing/2025-09-28-notes-on-advanced-perspective %})

## 图像平面、视点和视线方向（image plane, viewpoint & direction of view）

### 调整视线方向对于物体透视所产生的变化（Object Orientation to the Direction of View）

假设画面中有一个出现在观察者正前方的物体，当我们在水平方向将direction of view从正前方移向其他方向时，物体在画面中所呈现的图形随即从一点透视变为两点透视。

![effect of changing only the direction of view.jpg]({{site.baseurl}}/assets/images/effect of changing only the direction of view.jpg)

### 地平线和视点的关系（Horizon Line and Viewpoint）

An important and useful fact of linear perspective is that objects at the same height above the ground plane as the viewpoint are intersected in the image plane by the horizon line.

![horizon line and viewpoint in landscape perspective.PNG]({{site.baseurl}}/assets/images/horizon line and viewpoint in landscape perspective.PNG)

## 透视形变（perspective distortions）

### 透视缩短形变（Foreshortening Distortions）

![foreshortening and the triangular proportions.png]({{site.baseurl}}/assets/images/foreshortening and the triangular proportions.png)

**平移产生的透视缩短**

In **shift foreshortening**, a two dimensional surface is shifted away from the direction of view (the principal point) but remains parallel to the image plane; the actual surface *always* appears foreshortened because it is at an oblique angle to the viewpoint.

**旋转产生的透视缩短**

In **rotation foreshortening**, the surface is rotated so that it is no longer parallel to the image plane; the actual surface may or may not appear foreshortened, depending on whether it is at an oblique or perpendicular angle to the viewpoint.

These different types of foreshortening have different perspective effects.

![perspective image of flat forms.png]({{site.baseurl}}/assets/images/perspective image of flat forms.png)

**shift foreshortening has no effect on the perspective image of a two dimensional surface parallel to the image plane**

在空间中与画面平行的平面图形在保持与画面距离不变的情况下进行任意平移所导致的透视缩短并不改变该图形在画面中的形状和尺寸。换句话说，对于一个空间中的与画面平行的平面图形，将其在其所在的平面上任意挪动，该平面出现在画面中的大小将保持不变，哪怕超出了90度视锥。

The figure above shows the correct perspective projection of an identical row of windows (center). In the top row, the windows are kept parallel to the image plane but become increasingly oblique to the direction of view (*shift foreshortening*); in the bottom row, the windows are rotated in place to remain perpendicular to the viewpoint, which puts them at an oblique angle to the image plane (*rotation foreshortening*).

Surprisingly, even though it produces a foreshortened view of the actual two dimensional object, **shift foreshortening has no effect on a perspective image**. A window shifted 45° to one side is exactly the same size *on the image plane* as a window centered on the direction of view. This occurs because, at the location of the perspective image of the window, **the image plane is also foreshortened** by the same oblique angle of view, and this "secondary" foreshortening matches the foreshortening seen in the surface.

这是因为观察者在观看画面时，画面本身在进入观察者眼里时同样会产生透视缩短，而画面中的图形与观察者眼睛之间的视角倾斜程度（oblique angle of view）刚好使该图形在进入观察者眼睛后投影出正确的透视图形。

In contrast, **rotation foreshortening *always alters* the perspective image**. The image becomes "distorted" in the direction *perpendicular to the axis of rotation,* regardless of whether the object is central or peripheral in the circle of view and even when the rotation eliminates any foreshortening in the actual object! Remember: rotation foreshortening is still a completely correct perspective view of the rotated object, when viewed from the center of projection; it just *looks wrong* when we view the image from farther away.

The objectionable perspective distortions occur in the oblique view of a three dimensional object that has only been shift foreshortened on the image plane. In these cases, what "rotates" is not the plane surface of a two dimensional object but our view of a plane cross section through its three dimensional form.

将一个三维物体（而不是二维的平面图形）的斜视图在图像平面上仅进行“平移缩短”处理时，会出现令人不适的透视形变。在这种情况下，发生“旋转”的不是二维物体的平面表面，而是三维形体中的某个平面截面。

![perspective image of rounded forms.png]({{site.baseurl}}/assets/images/perspective image of rounded forms.png)

From [https://en.wikipedia.org/wiki/Perspective_distortion](https://en.wikipedia.org/wiki/Perspective_distortion):

![Camera_focal_length_distance_house_animation.gif]({{site.baseurl}}/assets/images/Camera_focal_length_distance_house_animation.gif)

Simulation showing how adjusting the angle of view of a camera, while varying the camera's distance and keeping the object in frame, results in vastly differing images. At narrow angles and long distances, light rays are nearly parallel, resulting in a "flattened" image. At wide angles and short distances, objects appear foreshortened or distorted.

### Cures for Perspective Distortions

古典壁画会尽量将画面保持在60度视锥之内，以避免出现明显的透视形变，影响画面美感。如果画中出现了一定程度的透视形变，画家便会人为的"修正"这些形变。比如在拉斐尔的壁画中，他将画面中的每个人物都以其自身为视觉中心来按照一点透视进行绘制，与背景的透视形变相脱离；他还将右下角本来因为透视形变会变成椭圆形的球体画成了标准的圆形；此外，他会巧妙地中画面中合适的地方安排人物，以遮挡背景中的建筑上可能出现透视形变的部分（比如画面中心的走廊被正前方的两位人物遮住；左右两根立柱的顶部被现实中的圆顶挡住；地面的瓷砖被各种人物遮挡）。

![IMG_0098.jpeg]({{site.baseurl}}/assets/images/IMG_0098.jpeg)

All figures are drawn as if centered on the direction of view — that is, with no perspective distortion. This is easiest to see in the two astronomers shown holding celestial globes (at right). Both figures are located at the righthand edge of the fresco, beyond the 30° circle of view. Rather than draw the spheres with the correct but elliptical perspective projections, Raphael simply drew them perfectly round.


