---
title: '记一次成功在CRT上播放带左右黑边的16:9视频的折腾经历'
category: computer
tags: 'crt corelec kodi android-tv 16:9 4:3'
published: true
---
### 背景

很多早年的TVB香港电视剧内容是4:3的，但是视频本身的画面比例是16:9的，原因是视频在画面左右两边自带了黑边。

当我尝试使用Android TV连接CRT电视播放这些TVB港剧时，无论使用哪种播放软件（jellyfin、kodi、VLC等）对视频画面进行哪种调整（满屏、覆盖、填充等），都无法让4:3的画面内容充满屏幕。

![16-9-content-with-bars-on-crt.jpg]({{site.baseurl}}/assets/images/16-9-content-with-bars-on-crt.jpg)


### 转机

一天晚上当我在iPad上再次尝试全屏看TVB港剧时，惊喜地发现使用jellyfin的覆盖画面选项居然可以满屏显示4:3的画面内容。

![tvb-fullscreen-on-ipad.png]({{site.baseurl}}/assets/images/tvb-fullscreen-on-ipad.png)

这让我开始思考这两台设备之间的差别。很快我就想到，这是因为iPad本身的屏幕分辨率就是4:3比例的，当选择覆盖画面选项时，jellyfin便会将左右超出画面的内容裁掉，而Android TV无论是通过AV接口直接连接CRT（这种情况下只支持16:9的480p和570p）还是使用HDMI转AV转换器，系统都只支持16:9的屏幕分辨率比例（即使将其连接到CRT上，也是将视频内容以16:9比例在Android TV上播放，然后被CRT横向压缩成4:3比例在电视屏幕上显示出来，此时播放器依然会认为设备的显示比例是16:9）。

基于这一发现，我在想是否能通过kodi自定义画面比例来强行将4:3的画面内容拉伸成16:9再被CRT压缩回4:3。于是我尝试用kodi进行手动画面调节，结果无论进行哪种手动调整（显示分辨率、缩放、画面比例、调整过扫描边缘等），画面左右两边始终都有黑边（调整画面比例后，有时上下也会出现黑边）。

在我手动调节kodi各种画面设置几近绝望时，我注意到Android TV版的kodi的显示分辨率设置里只有1080p这一个选项。这让我想到，corelec版的kodi上印象中可以支持很多分辨率，如果用corelec连接CRT播放视频，说不定能支持4:3的原生显示分辨率。

### 解决方案

于是我将装有corelec固件的u盘插到Android TV上，连接CRT电视后启动corelec系统。进入系统设置后，发现果然corelec的分辨率选项特别全（甚至支持4K)。于是我将分辨率设为4:3比例的800x600（或1024x768），将画面比例选择为原始大小，这时corelec就可以满屏播放自带左右黑边的16:9版本的4:3视频了。

![4-3-content-on-crt.jpg]({{site.baseurl}}/assets/images/4-3-content-on-crt.jpg)

终于可以在CRT上满屏播放自带左右黑边的TVB电视剧了！真是泪目。看来最强的视频播放解决方案还是得corelec。

## 题外话

在使用corelec接CRT电视播放TVB电视剧的过程中，我还发现：

- corelec的缩放和画面比例设置都可以正常工作，相反Android TV版的kodi上这些设置怎么调画面都有问题，估计是因为Android TV本身只支持1080p分辨率，导致kodi能进行的画面调整有一定限制。corelec才是kodi真正该有的样子。
- 此外我还惊喜的发现，corelec竟然也能正常识别我的usb无线网卡，亲测可以正常连接并使用wifi播放视频。

在对比jellyfin和kodi的播放体验后，我有了如下感受：

- kodi相比于jellyfin，播放视频时加载速度更快，原因是kodi属于纯客户端播放器，服务端只需负责数据传输；而jellyfin的数据加载和部分播放逻辑在服务端，导致播放体验会受限于服务端性能。相比之下使用kodi作为纯本地客户端进行视频播放时，服务端处理压力更小，同时kodi作为本地客户端视频播放能力也更强。相比于可以网页播放的jellyfin，使用kodi进行视频播放唯一的局限就是需要安装客户端。当然，在适用的场景下，kodi相比jellyfin是更强大的播放方案。
