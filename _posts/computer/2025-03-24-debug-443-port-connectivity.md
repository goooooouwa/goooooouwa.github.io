---
title: 调试443端口连通性的经历
category: computer
tags: AC86U openwrt 443 port-forwarding
published: true
---
调试经历：

1. 上网搜索发现Xfinity似乎不屏蔽80和443端口；
1. 通过连通AC86U的https管理页面（使用443端口）来排除了AC86U（以及Xfinity）的原因；
1. 发现原来openwrt默认打开了https管理页面（使用443端口）而且无法通过UI修改（需要修改配置文件并重启uhttpd服务，详情请见：[openwrt修改后台访问端口及开启https](https://www.cnblogs.com/xiykj/p/17689405.html)）
