---
title: Moonlight串流的网络调试
category: computer
tags: moonlight streaming troubleshooting
published: true
---
由于我的一台X86小主机与其他设备不在同一内网（姑且称为内网A），无法在局域网完成配对，因此Automatic configuration的方式就行不通了，此时如果想通过moonlight串流就只有以下2种方式：

1. ZeroTier
1. Manual port forwarding

为了最佳的串流性能，我选择了Manual port forwarding（当然ZeroTier也设置好了，作为替代方案）。于是我对X86小主机所在内网A进行了如下设置：

1. 宽带申请公网IP
1. 主路由替代光猫拨号上网（以便接管WAN端口转发请求）
1. 主路由设置端口映射（UDP+TCP: 47984 - 48010）指向X86小主机IP
1. 旁路由设置DDNS以便能通过域名方式访问内网A（具体方法参考[这篇]({% post_url computer/2024-02-21-openwrt-ddns-tutorial %})文章）

至此我便可以在外网使用moonlight客户端远程串流X86小主机了，只需在moonlight客户端中添加DDNS绑定的域名即可。So far so good.

后来，由于我当前所在的另一内网（称为内网B）也有一台N卡游戏本，于是我也尝试对其进行外网串流的配置，结果导致从内网B使用moonlight客户端访问内网A的X86小主机时所需端口被占用了。接下来我会详细解释故障原因。

为了能在外网使用moonlight客户端远程串流内网B里的N卡游戏本，我对N卡游戏本所在的内网B进行了如下设置：

1. 宽带申请公网IP
1. 主路由替代光猫拨号上网（以便接管WAN端口转发请求）
1. 主路由设置端口映射（UDP+TCP: 47984 - 48010）指向旁路由IP
1. 旁路由设置端口映射（UDP+TCP: 47984 - 48010）指向N卡游戏本IP
1. 旁路由设置DDNS以便能通过域名方式访问内网B

在此设置下，我便无法在内网B使用moonlight客户端访问内网A的X86小主机了，错误提示是UDP+TCP: 47984 - 48010被所在网络阻止访问了。在排除了内网A的DDNS公网IP获取错误、端口被占用、与ZeroTier冲突等可能性后，我无意间发现，安装了moonlight客户端的手机通过蜂窝网络是可以成功串流X86小主机的，这说明问题出在内网B。于是我开始调试内网B的设置。

当我将旁路由的moonlight端口映射规则禁用后，问题就解决了，可以在内网B使用moonlight客户端访问内网A的X86小主机了。

我怀疑moonlight串流需要客户端所在网络和服务器所在网络均能使用UDP+TCP: 47984 - 48010来完成网络连接，由于我在内网B将UDP+TCP: 47984 - 48010端口映射到了N卡游戏本IP，便导致当我尝试从内网B使用moonlight客户端访问内网A的X86小主机时所需的端口被占用了（X86小主机尝试将请求发给moonlight客户端，但是请求被映射到了N卡游戏本IP）。

以上仅是我的推测，还有待进一步研究。至少连接X86小主机的问题是解决了。那么，剩下的问题就是，我该如何在外网使用moonlight客户端远程串流内网B里的N卡游戏本呢？这个我暂时打算使用Moonlight Internet Hosting Tool通过Automatic configuration的方式来远程访问N卡游戏本，因为我大部分时候游戏本是在身边的。希望这种方式能在不添加端口映射的情况下自动工作。有待验证。