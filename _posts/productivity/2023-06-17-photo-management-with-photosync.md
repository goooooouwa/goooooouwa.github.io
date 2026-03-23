---
published: true
title: Wirelessly Photo Transfer with PhotoSync
category: productivity
---
## Lstest update to my photo organizing workflows

I can now use PhotoSync to wirelessly transfer my photos directly to my NAS (via A-List WebDav). Below is the configuration I use and the end result.

## PhotoSync configuration

![](https://goooooouwa.eu.org:8143/static/images/photosync-webdav-configuration.jpg)

![]({{site.baseurl}}/assets/images/20260317_212714000_iOS.png)

![]({{site.baseurl}}/assets/images/20260317_212722000_iOS.png)

![]({{site.baseurl}}/assets/images/20260317_212848000_iOS.png)

![]({{site.baseurl}}/assets/images/20260317_213438000_iOS.png)

## Result folder & filename

![](https://goooooouwa.eu.org:8143/static/images/photosync-folder-filename-example.jpg)

## Comparision with photo transfer with USB cable

My previous workflow is using USB cable to transfer photos to PC than run some Linux commands to organize the photos. Below is a comparision of these 2 transfer methods:

- PhotoSync默认folder命名是“年/月/日”，与我期望的目录名不同，不过这可以自定义。
- PhotoSync不会单独存放不含exif的照片，因为PhotoSync总是能获得照片的拍摄日期，即使是截图。
- PhotoSync导出总文件大小小于数据线导出，因为PhotoSync同一个照片只会导出一份，而通过USB会导出同一张照片的2个不同宽高比的版本（类似一个4:3，一个16:9，前者文件大小更大）。不过，对于同一个照片或者视频文件本身，PhotoSync导出的大小和信息量跟数据线导出完全相同，没有丢失品质。
- PhotoSync导出的照片日期更准确，USB导出照片经过Linux commands处理后，可能得到的不是真正的拍摄日期。比如有一张2023-04-30拍摄的照片，USB导出并处理后被命名为2023-04-22.jpg。

结论：PhotoSync is better in every aspect.
