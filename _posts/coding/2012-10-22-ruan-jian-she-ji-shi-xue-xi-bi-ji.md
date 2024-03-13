---
category: coding
date: 2012-10-22
title: 《软件设计师》学习笔记
---

#《软件设计师》学习笔记

## 关系数据库规范化：函数依赖

![](https://goooooouwa.eu.org:8143/static/images/WwnWq9b.jpg)

![](https://goooooouwa.eu.org:8143/static/images/NrLAkyB.jpg)

产生冗余和异常的两个重要原因是部分依赖和传递依赖。关系模式的规范化处理就是将非 3NF 的 1NF、2NF 变换成为 3NF 或更高级别的范式的过程。

## PV 操作

简单版本：
信号量 S 表示资源量；
P 操作就是若还有资源，则占有一个；
V 操作就是释放一个资源。

复杂一点的版本：
信号量 S 为正数时表示资源量，负数时表示排队人数；
P 操作就是若还有资源则占有一个(S>0)，否则排在队伍后面(S=S-1)；
V 操作就是释放一个资源(S=S+1)，如果有人排队(S<0)就叫一个上来使用资源(S=S+1)。

## 连通图

一个图中如果任意两点是可达的，则称为连通图。

## 基本的设计模式

![](https://goooooouwa.eu.org:8143/static/images/Ab0bZAw.jpg)

![](https://goooooouwa.eu.org:8143/static/images/Hzw32ak.jpg)

## AOE 图

AOE 图各顶点所有进入边的活动均已完成，从它出发的边上的活动才可以开始。

## 结点的度等于其分支数

A tree with 'n' number of nodes has exactly 'n-1' branches or degree.

结点的度等于其分支数；
树的度等于其结点的最大分支数；
树的总度数等于结点数-1。

## 各种基本排序的时间复杂度

![](https://goooooouwa.eu.org:8143/static/images/YmH01Ne.jpg)

## 关系代数运算

π 投影运算 从关系中选取若干属性组成新的关系。（竖向选择）
σ 选择运算 从关系中选择满足条件的元组组成新的关系。（横向选择）
× 笛卡尔积运算 将左关系所有元组与右关系所有元组连接组成新的关系。（笛卡尔积可看作无条件连接）
ϕ 连接运算 从两个关系的笛卡尔积中选择满足条件的元组组成新的关系。（条件分为：θ 连接，等值连接和自然连接）
P.S. 关系=集合, 元组=记录

## 分层数据流图例图

![](https://goooooouwa.eu.org:8143/static/images/CA0Wazr.jpg)

## Java 异常处理

![](https://goooooouwa.eu.org:8143/static/images/dhUenfF.jpg)

（4）throw 语句用来明确地抛出一个＂异常＂。在 catch 子句进行异常处理。

## 序列图

序列图只显示对象间通信（messaging）的消息，不显示对象内部消息处理过程。所以当你看到一个类接到其他对象发送的消息却不做任何行为时，不要惊讶，它可能已经在内部将消息处理了。
