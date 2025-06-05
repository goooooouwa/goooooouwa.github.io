---
title: OMV不允许admin用户通过Samba访问共享文件夹
category: computer
tags: OMV samba admin
published: true
---
记录一个目前遇到的在OMV上创建Samba分享的issue

OMV出于安全考虑，不允许admin通过Samba访问OMV（只允许通过WebGUI访问）。

https://forum.openmediavault.org/index.php?thread/41021-is-somehow-possible-allow-admin-user-to-access-smb/

解决办法：创建其他普通用户（如，pi）来访问Samba共享目录。


