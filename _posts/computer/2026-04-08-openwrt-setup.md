---
title: OpenWrt旁路由设置
category: computer
tags: openwrt
published: true
---

## 1. 配置Openwrt旁路由网络设置
进入：网络 -> 接口 -> Lan
指定静态ip地址
网关地址：主路由ip
DNS地址：主路由ip
不使用DHCP
关闭IPV6
设置防火墙（Lan口打开ip动态伪装，添加路由规则）

## 2. 配置主路由网络设置
主路由默认网关：旁路由ip
主路由端口映射：指向旁路由ip

## 3. 端口映射
旁路由端口映射：指向具体服务ip
