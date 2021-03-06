---
date: 2011-08-29
title: 快排的核心：分区子程序
layout: post
category: coding
---

分区子程序一句话描述就是：以尾数为界，将小于它的部分和大于它的部分分隔开。

具体怎么分，i代表分界位置，j代表当前检测值，从头依次检查，当前值小于尾数就与分界位置后（i+1）的值交换位置，否则不动。

这样下来，小于尾数的值都被挪到分界位置前面，而大于尾数的则留在分解位置后面。最后将尾数插到分界位置，就完成了分区子程序的功能。

接着，递归调用分区子程序就实现了快排。平均复杂度为O(N*logN)。
快排的特点，或者说任何高效的排序算法的特点是，较少的比较次数。这是提升排序效率的核心。

排序算法的理论下界应该就是O(N*logN了，也就是说不可能有比这更快的。再快那就是O(N)了，那就是说增加一个数只带来常数时间的增加，换句话说，增加一个数只用进行一次比较。这是不可能的。

可能做到的，就是对其他方面性能进行针对性的调整，比如快排是就地排序，对内存的占用少，适合内存珍贵的环境。就是针对特定环境对算法优化，而不是优化算法本身，因为已经到极限了。
