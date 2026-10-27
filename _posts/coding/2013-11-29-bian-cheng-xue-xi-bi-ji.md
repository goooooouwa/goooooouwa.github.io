---
category: coding
date: 2013-11-29
title: 编程学习笔记
---

## Linux system cross-compiling dependencies

**Cross-tool = cross compiler & cross Binutils & target C library.**

cross compiler <= native toolchain & target C library

cross Binutils <= native toolchain

target C library <= target Linux kernel headers & bootstrap cross compiler

bootstrap cross compiler <= native toolchain

target Linux kernel headers <= none

**Target Linux system = target Linux kernel & target C library & target system applications( Busybox) & file system**

target system applications( Busybox) <= cross compiler & cross Binutils & target C library

file system <= native disk tool

target Linux kernel <= cross compiler & cross Binutils

note:

target means build target.

native means runs on host.

cross means runs on host, build product for target.

## Vim 的 ex 命令

以冒号开始的命令实际上是 ex 命令。ex 与 vim 命令是同一编辑程序的两个不同的用户界面。vim 提供面向屏幕的用户界面，而 ex 则提供面向命令行的用户界面。所有的 ex 命令均可在 vim 中使用。

## Application Protocols

World Wide Web: HTTP( Hypertext Transfer Protocol)

Streaming audio and video: RTP( Real-time Transport Protocol)

Instant messaging: XMPP( Extensible Messaging and Presence Protocol)

Voice communication: VoIP( Voice-over-Internet Protocol)

Online gaming: 文本协议：HTTP，二进制协议：Protocol Buffer, Apache Thrift

服务端软件其实大同小异，都需要接收请求，处理请求，返回请求。

## Bash expansion

在 bash 中，命令参数会先被 bash 处理，再传递给命令。参数如果是正则表达式则会被 bash 替换成满足该表达式的结果，如果希望正则表达式不会 bash 处理，整个传递给命令，则需用引号括起来，bash 不会处理引号内的内容。

## 理解 Gradle build script

![]({{site.baseurl}}/assets/images/nONnsql.jpg)

## Gradle Plugin Portal vs Maven Central Repository

Gradle Plugin Portal

存放 Gradle plugins, e.g. org.springframework.boot:spring-boot-gradle-plugin

Maven Central Repository

存放项目依赖，e.g. org.springframework.boot:spring-boot-starter-web

## Understand IDEA IDEs diff colors

![]({{site.baseurl}}/assets/images/MI94rMA.png)

## What’s IntelliSort

![]({{site.baseurl}}/assets/images/1KbnvF1.png)

If this option is enabled, you get a more convenient way to view merges by displaying the incoming commits first, directly below the merge commit.

## What is viewport?

Viewport 就是视窗的像素宽。浏览器会根据视窗的像素宽来对页面布局。
