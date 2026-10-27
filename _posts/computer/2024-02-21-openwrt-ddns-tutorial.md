---
title: openwrt旁路由设置动态DNS教程
category: computer
tags: openwrt ddns freedns
published: true
---

## openwrt DDNS设置步骤

1. 在DDNS基本设置中填入DNS服务提供商以及账号登录信息。

![DDNS基本设置]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/5.png)

2. 在DDNS高级设置中填入IP检测方式（由于是旁路由无法直接获取WAN IP，便选择使用URL方式获取公网IP）。

![DDNS高级设置]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/6.png)

3. 保存并应用设置后，回到概览页面，首次运行服务需要点启动按钮，后续修改需要点击PID按钮重启进程以便手动触发获取公网IP请求。
   ![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/8.png)

4. 触发获取公网IP请求后，可以在日志中查看请求结果，确保获取IP与公网IP一致即可。

![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/7.png)

如果发现修改的URL未生效，可以在修改后点击“保存”按钮（而非“保存并应用”按钮），然后点击页面右上角的“未保存配置项”，再点击“保存”。这种方式能确保配置文件修改生效。

## （可选）防止公网IP获取成代理服务器IP

如果代理导致公网IP获取成代理服务器IP，可以设置直连域名规则避免公网IP获取错误。

#### v2ray客户端设置直连域名的方法

1. 双击相应规则集进入规则集设置：

![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/1.png)

2. 双击direct domain规则进入路由规则详情设置：

![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/2.png)

3. 添加直连域名后保存。

![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/3.png)

#### openwrt SSR+设置直连域名的方法

![]({{site.baseurl}}/assets/images/openwrt-ddns-tutorial/4.png)
