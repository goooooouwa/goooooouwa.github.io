---
date: 2018-08-25
title: Peak traction/breaking forces vs Slip Ratio with different Slip Angle
layout: post
category: racing
tags: vehicle-dynamics
---

加速时，当车轮轻微打滑时的驱动力最大，此时 slip ratio ~= 0.2，车轮的转速略高于实际行驶速度/轮半径。

刹车时，当车轮轻微打滑时的驱动力最大，此时 slip ratio ~= -0.15，车轮的转速略低于实际行驶速度/轮半径。

![Imgur]({{site.baseurl}}/assets/images/MEL8odC.png)

总结就是，车轮轻微打滑时的驱动力和刹车力最高，比完全不打滑更快。

![Imgur]({{site.baseurl}}/assets/images/frjawKL.jpg)

注意，这里的打滑是行驶方向 longitudinal 的打滑，与突破最大侧向转弯力后的 latitudinal 打滑不同，后者只会降低侧向转弯力。所以加速和刹车时，轮胎的轻微打滑会提供更大的驱动力和制动力，但轮胎一定不能侧向打滑，否则侧向转弯力会只会下降。

问题是，在过弯时，此时存在一定侧向转弯力，如果轮胎 longitudinal 出现轻微打滑，轮胎处于与地面相对摩擦状态，则侧向也是摩擦状态，侧向转弯力就低于峰值侧向力。是否过弯时，longitudinal 方向的打滑会使侧向转弯力降低？

由刹车转变为过弯的过程中，轮胎抓地力会由 100% longitudinal 刹车力转变为 100% lateral 侧向过弯力，这个过程中如果时刻使用轮胎 100%抓地力，aka trail braking，则轮胎抓地力会分布在 longitudinal 和 lateral 两个方向上，比如 80% braking, 20% cornering，60% braking, 40% cornering，40% braking, 60% cornering，20% braking, 80% cornering，**这个 transition 的过程中，是否时刻轮胎 slip ratio 和 slip angle 都保持最优值，即-0.15 和 6 度？**

![Imgur]({{site.baseurl}}/assets/images/fsObfQt.jpg)

**Slip Angle**

Slip angle 并不是说轮胎真的打滑。slip angle 容易让人误会。它只是指当有侧向力作用于轮胎时，轮胎行驶方向和轮胎朝向之间的角度。Slip angle 越大，侧向力(过弯力)越大。也可以说，侧向力越大，slip angle 越大。

![Imgur]({{site.baseurl}}/assets/images/lrCLifq.jpg)

![Imgur]({{site.baseurl}}/assets/images/QtqYCxV.jpg)

![Imgur]({{site.baseurl}}/assets/images/YuSj9f2.jpg)

**Peak traction/breaking forces vs Slip Ratio with different Slip Angle**

To reach peak traction/breaking forces requires a higher and higher slip ratio as the slip angle is increased.

可以理解为，当车子侧向转弯力越大(slip angle 越大)，为了达到最大驱动力，驱动轮需要更大程度的(加速)打滑。当然，随着 slip angle 的增大，轮胎能提供的最大驱动力会随之减小。所以，slip angle 为 0，即直线行驶时，轮胎峰值驱动力最大。换句话说，当转弯时，slip angle 的存在，则峰值驱动力和制动力都会降低，这也符合 traction circle，make sense。

![Imgur]({{site.baseurl}}/assets/images/mTicKwG.jpg)

当然，转弯时 slip angle 不可能为 0，此时应该追求最大侧向转弯力以提供最大过弯速度，最大侧向转弯力出现在 slip angle 为 6 度左右。

Slip Angle vs Lateral force

![Imgur]({{site.baseurl}}/assets/images/h47xfRP.jpg)
