---
title: Switch版空洞骑士无限吉欧问题调试
category: gaming
tags: switch hollow-knight cheat overlay edizon
published: true
---
### 背景

我的大气层switch上的空洞骑士不知道为啥出生就有99999个吉欧（游戏货币），而且无论被什么怪攻击多少次都死不了，甚至可以不打怪无脑冲地图，很奇怪，而且毫无游戏体验。不明白这是为什么。

这游戏感觉像是被修改过，好像是开了某种作弊代码似的，可是我并不记得自己曾经打开过任何cheat。我一开始怀疑是游戏版本问题，于是在网上找了该游戏的各种不同版本，可试玩后发现结果也都一样。

### Aha moment

在安装Edizon cheat overlay的过程中，我注意到[教程](https://www.cfwaifu.com/edizon-cheats/)中的这么一句话：

By default, Atmosphere enables all cheats that can be found on your SD when launching a game. This can be changed via Atmosphere’s configuration files.


> For the best experience, open the /atmosphere/system_settings.ini file and change dmnt_cheats_enabled_by_default = u8!0x1 to dmnt_cheats_enabled_by_default = u8!0x0. If the file does not exist you can copy the template from /atmosphere/config_templates/system_settings.ini and change the line, remember to remove the ";" in front.

原来

### 试验


### 成果


### 题外话

当我在Google，Brave和DuckDuckGo等不同搜索引擎上搜索“switch hollow knight geo 99999"时，只有DuckDuckGo的第一条返回结果是Edizon cheats for switch hollow knight (including geo 99999)，而Google和其他搜索引擎的首页结果均无任何跟cheat有关的结果。这让我不禁怀疑这些商业搜索引擎对搜索结果进行了过滤。我也果断决定以后弃用Google，而改用DuckDuckGo。


https://github.com/tomvita/EdiZon-SE?tab=readme-ov-file
