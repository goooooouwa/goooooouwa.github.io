---
title: NGINX Proxy Manager的试用总结
category: computer
tags: nginx docker docker-compose nginx-proxy-manager
published: true
---

我目前管理nginx代理服务器的方式是将手写的nginx配置文件托管在Github，由于portainer[不支持在Deploy时构建镜像](https://portal.portainer.io/knowledge/can-i-build-an-image-while-deploying-a-stack/application-from-git)，每次想拉取repo最新代码，都需要删除上次构建的nginx镜像和容器，然后重新Deploy来强制拉取repo最新代码并构建镜像，操作起来比较麻烦。

在过去一段时间，我开始注意到一个名为Nginx Proxy Manager的docker应用。它在各种地方越来越频繁地被提及，很多人都极力推荐这个应用（比如，[这个](https://www.reddit.com/r/selfhosted/comments/1dmh3mt/comment/l9vyc0t/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)Reddit帖子）。

我想尝试这个Nginx Proxy Manager的想法已经在心里酝酿许久，今天终于决定动手尝试。

## 我的nginx使用场景

- 我有一堆本地网络上运行的docker服务希望通过nginx反向代理来支持通过HTTPS请求远程访问
- 其中有部分docker服务自身不带任何authentication，希望nginx可以提供基本的authentication（通过提供一个basic auth的UI界面要求用户输入）
- 没有自己的主域名，只有一个免费的二级域名（即子域名）
- 希望通过nginx在一个地方统一进行SSL证书管理

## 试用总结

一通操作下来，我成功的配置了一个proxy host，并将onenav通过nginx proxy manager暴露在公网上。

![nginx-proxy-manager-config.png]({{site.baseurl}}/assets/images/nginx-proxy-manager-config.png)

但是在使用过程中我逐渐发现nginx proxy manager对于我的使用场景存在的一些局限性。并且逐渐意识到通过图形界面来管理nginx配置可能没有想象中那么美好（当然这一点我之前也想到了，这也是我一直迟迟没有试用它的原因）。

### 局限性#1

NGINX Proxy Manager默认只支持通过配置多个subdomain来在同一个domain下代理多个服务，而不支持通过使用同一个subdomain但是不同端口的方式（而这恰好是我的使用场景，因为我没钱买独立域名，所以是使用的免费eu.org subdomain）。

我也尝试过用Custom Locations来支持多个服务的场景。不过很快发现，custom location还是需要自己写配置，而且更致命的问题是，很多服务本身并不支持以子目录的形式运行，比如sonarr：

> Configuring Nginx Proxy Manager (NPM) to serve applications like Sonarr under a subdirectory (e.g., mydomain.com/sonarr) can be challenging due to how certain web applications handle base paths. Many applications are designed to run at the root (/) and may not support being served from a subdirectory without additional configuration

来自：https://forums.unraid.net/topic/186683-nginx-proxy-manager-custom-location-help/

### 局限性#2

NPM的Basic Auth只能通过请求本身的header来传递，而不是向用户提供一个basic auth的UI界面要求用户输入。这也不符合我的使用场景。

此外，在不修改默认配置的情况下，我还遇到以下docker容器访问的问题：

1. Huginn不work（连不上mysql服务器）
1. Calibre也不work（可以访问主界面但是连接不上远程桌面）

## What are some alternatives to Nginx Proxy Manager? 

Alternatives to Nginx Proxy Manager include Traefik, Caddy, Apache HTTP Server, HAProxy, WinGate, and OpenResty. They are worth exploring to determine the best fit for your specific requirements and infrastructure. Bear in mind that these alternatives vary in features, performance, and configuration complexity.

以后可能会尝试一些其他的替代品，比如Traefik, Caddy，但也不会抱太大希望。其实，有时候通过命令行、代码和配置比通过图形界面更灵活更方便也更强大。

比如，假如你有60个proxy host的配置需要迁移到另一个域名，通过界面会非常费时，而命令行就可以很快完成。

> I have just finished transferring 60 proxy hosts to another domain through NPM, manually via the GUI. It wouldn't work if I bulk changed the nginx configs themselves, it would just result in server errors on NPM.

> If I was using plain nginx, it probably would've taken me a second to do the domain switch with configs alone.

来自：https://www.reddit.com/r/selfhosted/comments/18jp6k3/comment/kdlnchq/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button

## 其他收获

这一次试用nginx proxy manager的另一个收获是学会了通过配置default network的方式来大大的简化对各个docker服务的`docker-compose.yml`的networks配置的修改工作量。而且我学习到，如果docker镜像自身已经expose了某些端口，那就不用额外的写expose语句来重复操作了（只要nginx跟docker服务在同一个network便能够直接访问的docker容器expose的端口），更不用添加ports指令的在网络上暴露端口。

这样下来，以后如果有新的docker容器希望通过nginx反向代理，只需要在容器的`docker-compose.yml`的最后添加如下一段全局默认network配置即可：

```
networks:
  default:
    name: nginx_default
    external: true
```

参考：https://docs.docker.com/compose/how-tos/networking/
