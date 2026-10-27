---
title: 通过Openwrt上安装ZeroTier实现异地访问局域网设备
category: computer
tags: openwrt zerotier
published: true
---

## 操作细节

1. Openwrt ZeroTier基本设置

![]({{site.baseurl}}/assets/images/openwrt-zerotier-access-lan-devices/1%20openwrt-zerotier-settings.PNG)

2. 为ZeroTier创建一个新的接口作为DHCP客户端

![]({{site.baseurl}}/assets/images/openwrt-zerotier-access-lan-devices/2.1%20create-new-interface-for-zerotier-dhcp.PNG)

![]({{site.baseurl}}/assets/images/openwrt-zerotier-access-lan-devices/2.2%20zerotier-dhcp-firewall-settings.PNG)

3. 为ZeroTier新的DHCP客户端接口添加防火墙规则

![]({{site.baseurl}}/assets/images/openwrt-zerotier-access-lan-devices/3%20add-firewall-rules-for-zerotier-dhcp-interface.PNG)

4. 在ZeroTier上为本地局域网添加指向Openwrt虚拟IP的Default Route

![]({{site.baseurl}}/assets/images/openwrt-zerotier-access-lan-devices/4%20add-zerotier-default-route.PNG)

## 参考教程：

1. OpenWrt 通过安装 ZeroTier 实现异地组网教程：[https://opclash.com/article/198.html](https://opclash.com/article/198.html)
1. ZeroTier+Openwrt 内网穿透配置| WAN口配置: [https://eller.top/post/94](https://eller.top/post/94)

## 关于如何使用ZeroTier作为VPN

ZeroTier本身并不提供VPN能力

The ZeroTier Cloud does not offer a path to the Internet. It is not a VPN solution which will allow you to pretend to be in another location. Every ZeroTier client still needs its own viable path to the Internet.

来自ZeroTier Topology 3：[https://sensorsiot.github.io/IOTstack/Containers/ZeroTier/#topology3](https://sensorsiot.github.io/IOTstack/Containers/ZeroTier/#topology3)

### 使用ZeroTier作为VPN的操作方法

Overriding Default Route / Full Tunnel Mode: [https://zerotier.atlassian.net/wiki/spaces/SD/pages/7110693/Overriding+Default+Route+Full+Tunnel+Mode](https://zerotier.atlassian.net/wiki/spaces/SD/pages/7110693/Overriding+Default+Route+Full+Tunnel+Mode)
