---
published: true
title: 记录一次重装PVE的步骤
category: computer
tags: pve
---
## 记录这次PVE重装的所有步骤

1. Backup all vms in Stop mode to an external drive (e.g. NAS)
2. 将网口连接网线以便PVE自动识别IP
3. Reinstall PVE (all data cleared)  
	- set maxvz as 0 (no local-lvm data)
	- set domain as pve@example.com
4. [Remove local-lvm](https://icn.ink/pve/20.html) (no need to do if set maxvz as 0)
5. `lvextend -rl +100%FREE /dev/pve/root` ([resize pve/root](https://foxi.buduanwang.vip/virtualization/pve/1434.html) to take the whole disk space)
6. 在数据中心中添加external drive and restore all vms
7. (Optional) [PCI passthrough](https://youtu.be/t_1o0rM3S7o?si=wey-mHQo953OEHhn&t=766)
8. (Optional) 设置[动态IP地址和网关](https://forum.proxmox.com/threads/set-a-dynamic-address-to-pve.119847/)
9. Upload SSL certificate
10. Enable 2FA
11. Enable repo for [pve-no-subscription](https://pve.proxmox.com/wiki/Package_Repositories#_proxmox_ve_7_x_repositories) & Disable pve-enterprise-subscription

## 关于USB硬盘休眠

如果想让虚拟机（比如OMV）自动休眠所连接的USB硬盘，需要在使用USB硬盘的虚拟机（如OMV）里安装hd-idle。

通过`/etc/fstab`挂载到虚拟机（比如OMV），开机后硬盘可能会持续运转（硬盘等持续闪烁），一段时间后会停止运转（硬盘灯常亮），10分钟后会自动休眠（硬盘灯呼吸）。

如果硬盘超过10分钟仍不休眠，依次尝试以下步骤：
1. 在虚拟机（如OMV)中禁用磁盘相关设置，包括：  
	- 高级电源管理
	- 停转时间
1. ~~PCI直通~~
1. ~~在PVE上安装hd-idle~~ (no need)
