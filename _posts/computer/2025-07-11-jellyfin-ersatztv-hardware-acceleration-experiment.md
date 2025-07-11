---
title: Jellyfin和ErsatzTV在Windows实机上硬件加速的一次尝试
category: computer
tags: jellyfin ersatztv hardware-acceleration transcode
published: true
---
我的硬件是J4125迷你主机，采用在Windows实机（非虚拟机）环境下安装Jellyfin和ErsatzTV。

## Jellyfin转码成功

经验证，Jellyfin可以成功转码（如下图所示）。

![jellyfin-web-player-transcode-information.png]({{site.baseurl}}/assets/images/jellyfin-web-player-transcode-information.png)

![cpu-gpu-resource-usage-when-transcoding.png]({{site.baseurl}}/assets/images/cpu-gpu-resource-usage-when-transcoding.png)

Jellyfin官方推荐的硬件转码配置方案推荐顺序如下：

Apple ≥ Intel ≥ Nvidia >>> AMD*

其中，集成显卡方案中推荐的CPU配置如下：

CPU: Intel Core i5-11400, Intel Pentium Gold G7400, Intel N100, Apple M series or newer (excluding Intel J/M/N/Y series up to 11th gen)

独立显卡的方案因为Nvidia显卡对Linux支持不够友好，因此我暂时不考虑。Apple M系列我暂时也不考虑。i5功耗较高。综合而言，最适合我的是N100系列迷你主机。

注意，Jellyfin不推荐J系列CPU，包括J4125，原因是架构太老，对最新的视频编码格式支持不够全面。

来源：[https://jellyfin.org/docs/general/administration/hardware-selection/#server-with-integrated-graphics](https://jellyfin.org/docs/general/administration/hardware-selection/#server-with-integrated-graphics)

## ErsatzTV在Windows下未转码成功

ErsatzTV则是无法在Windows下成功转码。由于VA-API只支持Linux，所以Windows下只能选择QSV。但实际使用发现，J4125无法成功通过QSV进行转码，根据作者的推测是因为CPU太老了。

来源：[https://discuss.ersatztv.org/d/88-help-with-intel-igpu-gen9-htop-shows-ersatz-using-cpu-for-ffmpeg](https://discuss.ersatztv.org/d/88-help-with-intel-igpu-gen9-htop-shows-ersatz-using-cpu-for-ffmpeg)