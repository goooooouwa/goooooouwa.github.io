---
title: OMV主分区扩容
category: computer
tags: omv partition parted resize2fs gparted
published: true
---

OMV 主分区扩容本质上需要以下 3 步：

1. 硬盘上分区后面存在可用的未分配空间（比如对于 PVE 虚拟机可以使用磁盘操作调整磁盘大小）
1. 扩大分区大小（比如使用 parted 命令）
1. resize 文件系统来使用全部分区大小（比如使用命令 resize2fs）

有 2 种方式进行分区扩容操作：

1. [Linux 系统通过命令行给主分区扩容](https://forum.openmediavault.org/index.php?thread/41271-expand-file-system-size-to-disk-size/)
1. [OMV 通过 GParted Live 图形界面给主分区扩容](https://www.wnark.com/archives/118.html)

![IMG_4196.JPG](https://goooooouwa.eu.org:8143/static/images/IMG_4196.JPG)

OMV 通过 GParted Live 扩容的具体步骤如下：

1. 安装 [kernel 插件](https://wiki.omv-extras.org/doku.php?id=omv6:omv6_plugins:kernel)
1. 安装 GParted Live ISO
1. 重启到 GParted Live 一次
1. 一路确认进入 GParted Live 图形界面
1. resize 分区
1. apply
