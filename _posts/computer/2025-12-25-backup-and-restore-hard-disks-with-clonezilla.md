---
category: computer
tags: clonezilla backup hdd
published: true
title: 如何使用Clonezilla备份与恢复硬盘
---
本教程所使用的工具：Clonezilla

## 方法一：备份整个磁盘

优点：速度慢

缺点：操作简单

### 硬盘备份步骤：

1. 将Clonezilla Live CD烧写到U盘里（如果是用的Ventory，则可以直接将Clonezilla ISO文件拷贝进Ventory镜像目录）
1. 将含有需要备份硬盘的电脑关机
1. 将Clonezilla启动盘插入含有需要备份硬盘的电脑上
1. 将电脑从Clonezilla启动盘启动
1. 设置语言和键盘
1. 选择device-to-image
1. (Option 1) 如果希望通过本地硬盘保存备份镜像，则直接将用来保存备份镜像的硬盘插入电脑，然后选择local disk选项
1. (Option 2) 如果希望备份到远程服务器，比如ssh server，则选择ssh server选项
  1. 填入服务器ip地址
  1. 填入服务器端口
  1. 填入服务器用户名
  1. 填入远程服务器用来保存备份镜像的文件夹路径（比如: /mnt/backup/backup/system/clonezilla-images）
  1. 确认服务器的安全性
  1. 填入服务器用户密码
1. 选择savedisk
1. 选择expert模式
1. 选中`-q1`选项（强制使用`dd`工具全盘备份硬盘，而不是`partclone`工具，使用`dd`可以放心不会有任何数据问题）
1. 完成备份

### 硬盘还原步骤：

1. 将电脑从Clonezilla启动盘启动
1. 设置语言和键盘
1. 选择device-to-image
1. (Option 1) 如果希望通过本地硬盘保存备份镜像，则直接将用来保存备份镜像的硬盘插入电脑，然后选择local disk选项
1. (Option 2) 如果希望备份到远程服务器，比如ssh server，则选择ssh server选项
  1. 填入服务器ip地址
  1. 填入服务器端口
  1. 填入服务器用户名
  1. 填入远程服务器用来保存备份镜像的文件夹路径（比如: /mnt/backup/backup/system/clonezilla-images）
  1. 确认服务器的安全性
  1. 填入服务器用户密码
1. 选择restoredisk
1. 选择expert模式
1. 取消任何自动进行的其他对分区数据进行的额外操作（比如auto grub install, auto resize partition, etc）
1. 完成还原

备注：

Clonezilla很聪明，它会默认选择与备份硬盘的文件系统最匹配的工具来进行备份和还原（比如如果是`partclone`所支持的文件系统，则会优先使用`partclone`来基于used sectors（含有效数据的扇区）进行备份，好处是能够针对各种不同的情况进行针对性的数据处理（比如自动运行grub install以确保新系统可以正常启动），备份的速度更快，生成的文件也更小；但是另一方面，Clonezilla的“自作聪明”有时候也会产生一些令人意料之外的效果。

我之所以强制使用`dd`工具进行备份，并且在还原系统时选择取消Clonezilla自动对分区数据进行的额外操作，是因为我的Elementary OS在使用`dd`备份后，使用beginner mode的默认参数还原硬盘后，发现Elementary OS里的flatpak应用的icon都消失了，说明clonezilla自动对分区数据进行的额外操作也可能对数据带来一些潜在的影响；在使用expert mode并且取消了clonezilla自动对分区数据进行的一系列额外数据操作后，还原的硬盘则是完美一比一的还原了我的Elementary OS系统。