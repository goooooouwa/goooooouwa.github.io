---
title: OMV网络设置和调试方式
category: computer
tags: homelab omv network
published: true
---
在OMV中修改网络设置有2种方式：

1.GUI（网络 -> 接口）
2.命令行工具omv-firstaid

运行omv-firstaid的方式：

1. Login using admin or equipvalent account
1. type `su` and login as su using admin password
1. type `sudo omv-firstaid`
1. Once windows from omv-firstaid pop up select reconfigure option

如果修改后依然无法正常联网，请检查以下事项：

1.Openwrt是否打开了服务；
2.Openwrt是否选择正确的服务器和模式（之前选成了海外回国）；
3.命令行wget google.com是否能正确解析网站DNS获得内容（不要使用ping google.com，即使在网络能够正常访问情况下，也不会ping成功）。 