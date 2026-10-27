---
title: 如何搭建Shadowsocks服务
layout: post
category: coding
tags: vpn shadowsocks
---

## 服务端安装 Shadowsocks

跟着[官方教程](https://github.com/shadowsocks/shadowsocks/tree/master)运行以下命令：

```
apt update

# if you don't have git installed
apt-get install git

apt-get install python-pip
pip install git+https://github.com/shadowsocks/shadowsocks.git@master
```

到此 shadowsocks 安装成功。

### 配置

复制官网教程的基本配置，后台运行 shadowsock，服务端就 OK 了。

## 客户端

iOS 客户端官网推荐的[Outline](https://itunes.apple.com/app/outline-app/id1356177741)（美国 App Store 免费下载）。我简单搜索了一下，中国区商店一类 shadowsocks 客户端貌似都下架了。

### 配置信息二维码生成说明：

根据官方的配置说明，可以看到 SS 协议采用的协议格式为：

`ss://method[-auth]:password@hostname:port`

并且采用 BASE64 的加密方式对 SS 协议的内容进行加密操作`method[-auth]:password@hostname:port`，然后再与`ss://`进行拼接即可。

`ss://BASE64-ENCODED-STRING-WITHOUT-PADDING`

可以在 Chrome Console 中使用 JavaScript 的`btoa()`方法进行 base64 编码，如下：

![]({{site.baseurl}}/assets/images/SSzucyN.png)

例如，将`ss://bf-cfb-auth:test@192.168.100.1:8888`，这个内容转换成标准的 SS 协议内容就成了：

`ss://YmYtY2ZiLWF1dGg6dGVzdEAxOTIuMTY4LjEwMC4xOjg4ODg=`

然后直接将这段字符串生成二维码即可。

## Update 2019-07-18

Bandwagon 推出了一款专用于 Shadowsocks 的服务，Just My Socks，价格比 VPS 稍贵。该服务提供域名连接，会定期更换 IP，再也不用因为 IP 被封所烦恼了。

## Update 2019-02-28

用了 5 天 VPS 的 IP 就被封了，网上搜了一通发现 2017 年就有人反应 shadowsocks[被封 IP 的问题](https://github.com/shadowsocks/shadowsocks/issues/993)，看来作者被请喝茶之后，Shadowsocks 基本就被 ZF 掌握了。

换了一个 IP，如果短时间再被封，就放弃 shadowsocks 了。网上又推荐[v2ray](https://github.com/v2ray)，以后再看吧。

---

## 购买 VPS

跟着教程选择 VPS，结果发现搬瓦工 10G $19.99/yr 的套餐下架了，最便宜的 20G $49.99/yr（342.62 元）；Vultr 最便宜的$3.5/mon，算下来$42/yr（287.86 元/年），稍微便宜一点。

准备买 Vultr，比较了一下服务器，湖北电信 ping 洛杉矶的服务器[延迟最低](https://zhuanlan.zhihu.com/p/38166614)，[另一篇文章](https://www.cnvultr.com/368.html)也印证这一点。

在 Vultr 界面选择洛杉矶，结果下面没有$3.5/mon 套餐，最便宜的套餐是$5/mon ($60/yr)。很郁闷，是不是过个年也准备涨价了？给 Support 发了封邮件，秒回:

> ...currently sold out in that location ...
> the new capacity will be online within the next 2 to 4 weeks.

于是换了几个服务器试了一下，只有 Atlanta 下面有$3.5 套餐。觉得有点坑爹，又在网上搜了一下搬瓦工和 Vultr 的对比，感觉旗鼓相当，决定就选搬瓦工，先入为主吧。

于是买了半年$25.99（176 元）的 Los Angales 服务器。继续跟着教程进行下一步。

## 中间的曲折

打开搬瓦工服务器管理界面，竟然找不到第一个教程里的"Shadowsocks Server 选项"。没办法，找到官网，跟着[说明](https://github.com/shadowsocks/shadowsocks/blob/master/README.md)进行安装。

```
#CentOS:

yum install python-setuptools && easy_install pip
pip install git+https://github.com/shadowsocks/shadowsocks.git@master
```

第一个命令成功，结果运行第二个命令 pip 报了 Syntax error。即使单独运行 pip 也会报同样的错误，输出如下：

```
[root@host ~]# pip
Traceback (most recent call last):
File "/usr/bin/pip", line 9, in <module>
load_entry_point('pip==19.0.2', 'console_scripts', 'pip')()
File "/usr/lib/python2.6/site-packages/pkg_resources.py", line 299, in load_entry_point
return get_distribution(dist).load_entry_point(group, name)
File "/usr/lib/python2.6/site-packages/pkg_resources.py", line 2229, in load_entry_point
return ep.load()
File "/usr/lib/python2.6/site-packages/pkg_resources.py", line 1948, in load
entry = __import__(self.module_name, globals(),globals(), ['__name__'])
File "/usr/lib/python2.6/site-packages/pip-19.0.2-py2.6.egg/pip/_internal/__init__.py", line 19, in <module>
from pip._vendor.urllib3.exceptions import DependencyWarning
File "/usr/lib/python2.6/site-packages/pip-19.0.2-py2.6.egg/pip/_vendor/urllib3/__init__.py", line 8, in <module>
from .connectionpool import (
File "/usr/lib/python2.6/site-packages/pip-19.0.2-py2.6.egg/pip/_vendor/urllib3/connectionpool.py", line 92
_blocking_errnos = {errno.EAGAIN, errno.EWOULDBLOCK}
                                ^
SyntaxError: invalid syntax
```

不知道什么原因，网上也没搜到好的回答，决定重装一下 CentOS（目前是 centos 6 x86），网上搜了个[教程](https://segmentfault.com/a/1190000010528542)，重装了系统到 centos 6 x86_64。突然想到，之前的报错是不是安装包之前没有运行`yum update`？哎...程序员的工具体验真是差。

系统重装后，赶紧先运行一下`yum update`。重新尝试，结果还是不行，同样的错误。

崩溃...

最后还是换了 Ubuntu，然后一下子就安装成功了。还是 Ubuntu 对新手友好。安装完了，才看到 shadowsocks[中文教程](https://github.com/shadowsocks/shadowsocks/wiki/Shadowsocks-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)上有一句：

> 除非有明确理由，不建议用对新手不友好的 CentOS。

...

## 参考：

- https://moshuqi.github.io/2017/07/20/自己搭建VPN服务器
- http://www.zliu633.com/2018/07/13/%E4%B8%AA%E4%BA%BAvpn%E7%9A%84%E6%90%AD%E5%BB%BA%E6%96%B9%E6%B3%95-mac-os/
- https://blog.csdn.net/lecepin/article/details/52063843
- https://segmentfault.com/a/1190000010528542
- https://github.com/shadowsocks/shadowsocks/blob/master/README.md
- https://shadowsocks.org/en/download/clients.html
- https://zhuanlan.zhihu.com/p/38166614
- https://www.cnvultr.com/368.html
