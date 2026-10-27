---
date: 2018-02-12
title: 汽车物理学
layout: post
category: racing
---

两档位之间的 Gear ratio 差距决定了换挡后引擎转速会有多少差距，不同两挡之间 ratio 差距不同，因此转速回落大小也不同。一档升二档，齿比差距较大，转速落差更大。三档升四档，齿比差距较小，转速落差更小。

转动运动如果没有力的作用，会保持角速度不变的旋转。

引擎的转速和扭矩可以直接换算成车轮行驶的速度和牵引力加速度，因为驱动轴 crankshaft 跟驱动轮轴之间只是简单的齿比关系。想象一个大齿轮匹配一个小齿轮 ⚙️⚙️。

## 不同档位，引擎扭矩、转速与轮上扭矩和转速以及车速的关系

The combination of gear and differential acts as a multiplier from the torque on the crankshaft to the torque on the rear wheels. For example, the Corvette in first gear has a multiplier of 2.66 _ 3.42 = 9.1. This means each Newton meter of torque on the crankshaft results in 9.1 Nm of torque on the rear axle. Accounting for 30% loss of energy, this leaves 6.4 N.m. Divide this by the wheel radius to get the force exerted by the wheels on the road (and conversely by the road back to the wheels). Let's take a 34 cm wheel radius, that gives us 6.4 N.m/0.34 m = 2.2 N of force per N.m of engine torque. Of course, there's no such thing as a free lunch. You can't just multiply torque and not have to pay something in return. **What you gain in torque, you have to pay back in angular velocity.** You trade off strength for speed. For each rpm of the wheel, the engine has to do 9.1 rpm. The rotational speed of the wheel is directly related to the speed of the car (unless we're skidding). One rpm (revolution per minute) is 1/60th of a revolution per second. Each revolution takes the wheel 2 pi R further, i.e. 2 _ 3.14 \* 0.34 = 2.14 m. So when the engine is doing 4400 rpm in first gear, that's 483 rpm of the wheels, is 8.05 rotations per second is 17.2 m/s, about 62 km/h.

![Imgur]({{site.baseurl}}/assets/images/oRBnIEb.jpg)

这个图的彩色曲线是车轮转速和扭矩之间的关系(油门全开时)，黑色是引擎转速和扭矩关系。

下图是斯巴鲁 BRZ 的轮上扭矩的曲线：

![Imgur]({{site.baseurl}}/assets/images/dEU7rW6.jpg)

高尔夫 GTI 2.0T+DSG 的轮上扭矩曲线：

![Imgur]({{site.baseurl}}/assets/images/zG7Xi4S.jpg)

结合全油门轮上扭矩图和下面的 Engine Torque vs Throttle map 可以绘制出各种油门开度下的轮上扭矩图。

![Imgur]({{site.baseurl}}/assets/images/mrKze3L.png)

**重视加速性的换挡策略**下，在某一油门开度，最佳换挡时机是，当前档位与下一档位轮上扭矩曲线之间的交叉点对应的引擎转速。如果油门开度变化，则换挡时机随着新的轮上扭矩曲线交叉点的变化而变化。油门开度越小，换挡时机越靠前，即换挡转速越低。**油门深度决定了换挡转速。**

**重视燃油经济性的换挡策略**下，最佳换挡时机是，油门开度在 0%到 70%之间时，约 1700 转换挡（尽量维持发动机在 1500 转左右运转），当油门开度为 70%到 100%之间，随着油门开度增大，逐步升高发动机换挡转速（如 70%时 2000 转，80%时 2700 转，90%时 4000 转），直到油门开度达到 100%之后，随意换挡（维持发动机在 4000 ～ 7000 转之间即可）。

可以比较，当一脚油门到底时，这两种换挡策略下，换挡时机的不同。

重视加速性的换挡策略

| 当前档位 | 油门深度 | 升档时机(rpm) |
| :------- | :------- | :------------ |
| 1        | 70       | 4000          |
| 2        | 80       | 5000          |
| 3        | 90       | 6000          |
| 4        | 100      | 7000          |

重视燃油经济性的换挡策略

| 当前档位 | 油门深度 | 升档时机(rpm) |
| :------- | :------- | :------------ |
| 1        | 70       | 1700          |
| 2        | 80       | 2500          |
| 3        | 90       | 4000          |
| 4        | 100      | 5000          |

我怀疑变速箱的换挡逻辑会根据油门开度来选择不同策略。至少在不同驾驶模式下（Echo, Comfort, Sport），变速箱换挡时机不一样，比如 Sport 下，即使轻踩油门，也会在 4000 转换挡。

想想带变速器的自行车，其实原理是一样的。骑车换挡时其实不会考虑最优换挡时机，只要觉得蹬得够快了就升档，觉得蹬不动就将挡。虽然最优换挡时机可能只有一个，但是允许换挡的时机却是一个区间。开车换挡感到顿挫，也许是档位间转速落差太大，还可能是换挡间油门控制不够平稳，还有可能是自动变速箱手动模式换挡 torque converter 结合较快，提供的转速匹配的时间较半集合更短。

原来，汽车厂家对一款车型的定位不一样，变速箱的换挡逻辑标定的也不同。比如说定位经济的车型，变速箱的标定上可能会让它积极升挡和延迟降挡；而定位运动的车型，在变速箱的标定上则是偏向于延迟升挡和积极降挡；定位舒适的车型，变速箱在标定上可能会尽量减少频繁换挡。这就是经济模式、运动模式和舒适模式。

## 油门深度 vs 换挡时机

For a given throttle in a given gear, there is a unique vehicle speed（车速 ～ 车轮转速～引擎转速） at which an upshift takes place (gear shift goal unknown). The simulation operates similarly for a downshift.

![Imgur]({{site.baseurl}}/assets/images/KPDoKlS.png)

查表可知：

| 当前档位 | 油门深度 | 升档时机(mph) | 降档时机 |
| :------- | :------- | :------------ | :------- |
| 1        | 90       | 38            | 无       |
| 2        | 20       | 30            | 5        |
| 3        | 40       | 53            | 25       |
| 4        | 50       | 70            | 50       |

### Fuel-Optimal Gear Shift Strategy

early and frequent upshift pattern for the transmission. It renders the engine, on average, to operate at a lower speed and high torque region, and hence improving the fuel economy.

![Imgur]({{site.baseurl}}/assets/images/WbFr33A.png)

### Driveability-Optimal Gear Shift Strategy

transmission tends to shift up late to ensure a driveability satisfaction.
Driveability measured by Power reserve = (Max Torque - Current Torque) \* Engine Speed

![Imgur]({{site.baseurl}}/assets/images/Ip41BCf.png)

a req, fit 红色的线表示 90%概率的加速需要，所以只要扭矩大于或等于这个加速度即可。所以 Method 3 的结论其实是说，重视加速性策略下，最佳换挡时机是一个区间，只要发动机扭矩维持在这个区间内，均可满足 90%的加速需要（由 a req, fit 表示）。

The **variable power reserve** concept reveals itself to be able to apply in realtime by a control approach, e.g. model predictive control [148], to **ensure a driveability satisfaction meanwhile still achieving a fuel economy benefit**.

**One of the key points in simplifying vehicle physics is to handle the longtitudinal and lateral forces separately**. Longtitudinal forces operate in the direction of the car body (or in the exact opposite direction). These are wheel force, braking force, rolling resistance and drag (= airresistance). Together these forces control the acceleration or deceleration of the car and therefore the speed of the car. Lateral forces allow the car to turn. These forces are caused by sideways friction on the wheels. We'll also have a look at the angular moment of the car and the torque caused by lateral forces.

## 典型起步加速和超车过程的油门动作、换挡逻辑、最终加速度和速度曲线

Table 2: Throttle schedule for first simulation (passing maneuver)

| Time (sec) | Throttle (%) |
| :--------- | :----------- |
| 0          | 60           |
| 14.9       | 40           |
| 15         | 100          |
| 100        | 0            |
| 200        | 0            |

The first column corresponds to time; the second column corresponds to throttle opening in percent. In this case no brake is applied (brake torque is zero). The vehicle speed starts at zero and the engine at 1000 RPM. Figure 12 shows the plot for the baseline results, using the default parameters. As the driver steps to 60% throttle at t=0, the engine immediately responds by more than doubling its speed. This brings about a low speed ratio across the torque converter and, hence, a large torque ratio (see Figure 6 and Figure 11). The vehicle accelerates quickly (no tire slip is modeled) and both the engine and the vehicle gain speed until about t = 2 sec, at which time a 1-2 upshift occurs. The engine speed characteristically drops abruptly, then resumes its acceleration. The 2-3 and 3-4 upshifts take place at about four and eight seconds, respectively. Notice that the vehicle speed remains much smoother due to its large inertia.

![Imgur]({{site.baseurl}}/assets/images/ZAl5NJD.png)

Figure 12: Passing maneuver simulation time history

At t=15sec, the driver steps the throttle to 100% as might be typical of a passing maneuver. The transmission downshifts to third gear and the engine jumps from about 2600 RPM to about 3700 RPM. The engine torque thus increases somewhat, as well as the mechanical advantage of the transmission. With continued heavy throttle, the vehicle accelerates to about 100 mph and then shifts into overdrive at about t = 21 sec. The vehicle cruises along in fourth gear for the remainder of the simulation. Double click on the ManeuversGUI block and use the graphical interface to vary the throttle and brake history.

![Imgur]({{site.baseurl}}/assets/images/hhu0mJ1.png)

### 高速转弯时的侧向加速度影响因素

The **sideslip angle b (bèta**) is the difference between the car orientation and the direction of movement. In other words, it's the angle between the longtitudinal axis and the actual direction of travel. So it's similar in concept to what the **slip angle** is for the tyres.

![Imgur]({{site.baseurl}}/assets/images/COiKwsi.jpg)

The following information is shown on screen:

- steering angle (also known as delta)
- side slip angle (also known as beta)
- "rotation angle" (due to yaw rate)
- slip angle front wheels
- slip angle rear wheels
- velocity vector relative to car reference frame
- velocity vector in world space

![Imgur]({{site.baseurl}}/assets/images/cPDix4h.jpg)
