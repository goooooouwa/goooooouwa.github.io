---
title: Home media server setup
category: computer
---

## Media Server

### Hardware

Raspberry Pi 3B + USB hard disk 

### Software

1. HTTP file server: nginx
2. Photo gallery: pigallery2 + nginx (tried piwigo, too slow and heavy for Pi)
3. File remote access: smb->sftp (tried Merlin router built in SMB, not doesn’t support ExFAT disk format)
4. Media server: Plex (tried smb, pro is mobile friendly, con is UI not friendly)
5. Download server: qBittorrent (tried
6. Transmission, no global trackers)
7. NAS: omv 5 (SMART, monitoring, not so many useful plugins)
8. DNS Ad blocker: AdGuard home (tried Pihole, UI not as intuitive; tried Diversion, broken for Merlin 386.3; overall DNS ad blocking is not so effective)

#### USB hard disk auto idling

hd-idle (tried hdparam, not working for USB disks)

#### Access over Internet

1. 破解电信光猫（获取superadmin），上网方式从路由改为桥接，关闭光猫无线功能，光猫仅仅做一件事情：桥接merlin路由器来拨号上网。（tried光猫上的端口转发，不work）
2. 路由器拨号上网
3. 其他路由器以AP模式接入主路由器
4. 其他路由器暂时关闭无线功能（一方面华硕主路由器信号已经不错，另一方面，没有Mesh功能，多个无线网络无法无缝漫游，以后需要再打开，手动切换）
5. 主路由器打开端口转发

#### All HTTPs connections (including merlin Router) with Let’s encrypt

1. Using DNS challenge (tried Merlin Router built in HTTP challenge approach, not working due to 80/443 ports blocked)
2. Freenom domain (tried freedns secondary domain, only primary domain supported; aliyun domain and DNS probably will also work, as it’s supported by merlin Router)
3. Freedns nameserver + ddns (tried CloudFlare, not supported by Merlin router)
4. acme.sh on Raspberry Pi

### Overall experience

Pros:

1. Always on
2. low power consumption
3. 不占桌面空间

Cons:

1. Weak compute power
2. No UPS auto shutdown (For now, if power down, sd card in Pi is possible to crupt, but since external USB is mostly idle, usually not write activities, should be fine if shutdown.)

ARM-based Mini Linux PC is the ideal home server. Merlin router is mostly good at 科学上网，其他网络应用要求更好的性能和存储空间以及更好的软件支持，最好用其他服务器（RPi or HTPC)。

## Game streaming server

### Hardware

Steamlink + Gaming laptop + Xbox one OG controller with wireless adapter


### Software

Steam

#### Wake on lan

1. Replace dead battery
2. Upgrade BIOS to support s5 (shutdown) wake on lan


#### Xbox one OG controller with wireless adapter

As xow is already bundled with steamlink, it should work. Caveats:
1. xow doesn’t support pairing, need to pair on pc before using on steamlink
2. VirtualHere conflicts with xow, need to stop sharing adapter in virtualHere

##### Steps to connect XBox one OG controller with wireless adapter:

1. Stream games on PC
2. Connect wireless adapter on pc
3. Pair with Xbox one OG controller
4. Unplug the wireless adapter
5. Plug in to steamlink
6. Unplug power to shutdown steamlink
7. Reconnect power to boot steamlink
8. Once booted, press button on wireless adapter and Xbox one controller sync button (the one on the side), should both light up and connected
9. Next time just press button on wireless adapter and the wake button(with logo) on Xbox one controller, should reconnect pretty fast.


## Previous home media server

### Hardware

old MacBook Pro + Ethernet adapter

### Software

1. Photo management: PhotoPrism (tried PhotoStructure, also good, though not as easy and powerful as PhotoPrism)
2. Download server: 迅雷

#### Wake on Lan (MacBook pro only support Ethernet wake on lan when lid closed)

1. Ethernet adapter
2. forward Port 9
3. Turn on Caffeine (to Keep Mac awake)

### Overall experience

Pros:

1. Powerful hardware
2. Support PhotoPrism (4g ram)
3. 迅雷下载速度快

Cons:

1. 占桌面位置
2. Not always on (need to Wake on Lan first to save power)

## Future upgrade considerations

### Server

Mini PC with UPS and more powerful hardware, probably with large internal storage (SSD & 2.5 hard disk)

### Storage

Hard disk or external hard disk? Both SATA interface, should work the same, right? Except external is easier to break.