---
date: 2018-12-25
title: 是否可以比计划中提前地准备下个月第1个iteration卡？
layout: post
category: agile
tags: agile product-management
---

## TLDR 
计划做得要尽可能的晚，降低实施前计划发生变化的可能性，提高计划的稳定性。所以即使可以提前，最好还是不要提前。

## Longer version 

只有识别出了某iteration中需要spike的卡才能知道某iteration中哪些卡是（没有风险）可以开始设计的，才能开始该iteration卡的准备。
而发现下个月第1个iteration中有哪些卡需要spike的最早时间点是敲定下个月的release plan的时候（更早的roadmap planning不可能发现所有的需要spike的点）。因此问题等价于：是否可以比计划中提前地敲定下个月的release plan？

理想情况下，下个月的release plan发生在这个月的第1个iteration的第2周的周一上午（这个月第2个iteration的IPM发生在这个月的第1个iteration的第2周的周一下午。两个会之间有几个小时可以准备spike卡的内容）。

而下个月的Release plan 最早只能发生在这个月的第1个iteration的第1周的周一上午，否则计划太远容易变。

回答推导问题：是否可以比计划中提前地敲定下个月的release plan？

可以。下个月的Release plan 最早可以发生在这个月的第1个iteration的第1周的周一上午，比计划中提前一周时间。只是这个时间点定的release plan会比理想时间下定的release plan早一周，稳定性会下降一些。

所以，回答原始问题：是否可以比计划中提前地准备下个月第1个iteration卡？

可以。最早提前一周（同时下个月的release plan提前一周，在release plan之后即可开始准备下个月第1个iteration卡）。只是这个时间点定的release plan会比计划中制定的release plan稳定性下降一些。


题外话
下个月的Release plan最晚发生在这个月第2个iteration的IPM之前，这样才能提前1个iteration将下个月release plan中需要spike的卡完成spike（保证release plan能按计划的卡优先级的顺序完成），否则只能将需要spike的卡挪到下个月的第2个iteration（影响release plan计划的卡的优先级顺序），当然这也勉强可以接受。



是否可以比计划中提前地准备下个月第2个iteration卡？

可以。最多可以提前2周（？）。因为在此之前spike已经完成了。只是卡的稳定性会下降（因为距离iteration真正发生的时间更远）。
但最好不要，因为计划中每个iteration已经提前2个迭代开始准备了。再提起计划内容的稳定性就太低了。