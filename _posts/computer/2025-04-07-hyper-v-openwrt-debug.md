---
title: Hyper-V Openwrt调试
category: computer
tags: openwrt hyper-v
---
issue：Openwrt 连接不上局域网，打不开页面。

尝试还原hyper v保存点，结果报错。报错信息：

> 尝试更改“新建虚拟机”的状态时应用程序遇到错误

> “新建虚拟机” 无法启动

无解，最后注意到有一个网口断开了，重新连接后就恢复了正常访问。怀疑该网口有故障，于是将hyper v的LAN虚拟适配器从原来的Eth 2网口改到Eth 3网口上面，希望以后会稳定。

# Update 2025/05/02

一段时间后同样的问题又出现了。检查了LAN虚拟适配器对应的网口确实是正常联网的，因此估计不是网口的问题。因为Hyper-V上的Openwrt目前只是备用（主要的Openwrt运行在另一台PVE服务器虚拟机里），决定放弃不管，以后有闲情再试试重装Immortal版的Openwrt试试。
