---
date: 2019-12-13
title: 如何使用vJoy + UCR来将键盘鼠标作为游戏控制器
category: gaming
---

# 如何使用 vJoy + UCR 来将键盘鼠标作为游戏控制器

Vjoy: 用来创建虚拟控制器驱动（光有它不能用键盘或鼠标控制控制器，还需要用映射工具将键盘鼠标按键映射到控制器按键）
UCR: Universal Controller Remapper，将键盘鼠标按键映射到控制器按键

Step 1: Download and Install Vjoy
Step 2: Setup Vjoy device (不要设为第 1 个设备，会跟实际插入电脑的控制器冲突）
![]({{site.baseurl}}/assets/images/ZqA9t8Z.png)

Step 3: Download and Install UCR
Step 3.1 Setup UCR
On first run of UCR, check the vJoy log to make sure vJoy loaded OK
From the UCR main menu: IOClasses -> vJoy -> Show vJoy log
If all went well, install the SCPVBus:
From the UCR main menu: IOClasses -> vJoy -> Install SCPVBus
If this step fails, open an admin command prompt and navigate to UCR's resources folder, there are .bat files in there
Step 4: 将键盘按键或者鼠标映射到控制器按钮或摇杆
4.1 将键盘按键映射到控制器按钮
4.1.1 选择 button to button，点击 add
![]({{site.baseurl}}/assets/images/eXrtnPQ.png)

4.1.2 映射键盘按键到控制器按钮
4.1.1 Input Button: 选择键盘按键
4.1.2 Output Button: 选择 vXBox Stick 2?（明确是模拟 XBox 控制器，我也不确定这里应该选择 vJoy Stick 2 还是 vXBox Stick 2，自己试一下吧）
4.1.3 Output Button: 选择 vXBox Buttons -> 具体 Button
![]({{site.baseurl}}/assets/images/uuZ87oi.png)

4.2.1 选择 Mouse to Axis（注意，不是 Axis to Mouse），点击 add
![]({{site.baseurl}}/assets/images/pgmcGmp.png)
4.2.2 映射鼠标到摇杆
4.2.2.1 Input: 选择 Any Mouse
4.2.2.2 Outputs: 选择 vJoy Stick 2
4.2.2.3 Outputs: 选择 vJoy Stick Axes -> 1(X)（左摇杆横向移动）
4.2.2.4 Outputs: 选择 vJoy Stick Axes -> 2(Y)（右摇杆纵向移动）
![]({{site.baseurl}}/assets/images/p1nBK66.png)
4.3 点击 Save Settings 保存设置
![]({{site.baseurl}}/assets/images/P4NZfr5.png)
Step 5: 可以使用设备管理器或者 Vjoy Monitor 来检查映射是不是成功
![]({{site.baseurl}}/assets/images/B40GrZV.png)
