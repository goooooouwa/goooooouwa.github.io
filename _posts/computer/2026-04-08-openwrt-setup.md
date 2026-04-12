---
title: OpenWrt旁路由设置
category: computer
tags: openwrt
published: true
---

## 1. 配置Openwrt旁路由网络设置
1. 进入：网络 -> 接口 -> Lan
1. 指定静态ip地址
1. 网关地址：主路由ip
1. DNS地址：主路由ip
1. 不使用DHCP
1. 关闭IPV6
1. 设置防火墙（Lan口打开ip动态伪装，添加路由规则）


## 2. 配置主路由网络设置
1. 主路由默认网关：旁路由ip
1. 主路由端口映射：指向旁路由ip


## 3. 端口映射
1.旁路由端口映射：指向具体服务ip
