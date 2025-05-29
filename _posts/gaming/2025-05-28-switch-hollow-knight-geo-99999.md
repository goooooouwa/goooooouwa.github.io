---
title: 记一次Switch版空洞骑士无限金币问题的调试经历
category: gaming
tags: switch hollow-knight cheat overlay edizon
published: true
---

### 背景

我的大气层switch上的空洞骑士不知道为啥出生就有99999个吉欧（游戏内金币），而且无论被什么怪攻击多少次都死不了，甚至可以不打怪无脑冲地图，很奇怪，而且毫无游戏体验。我不明白这是为什么。

![2025-05-28 19.23.05.jpg]({{site.baseurl}}/assets/images/2025-05-28 19.23.05.jpg)

这游戏就好像是被修改过，仿佛是开了某种作弊代码似的，可是我并不记得自己曾经打开过任何cheat。刚开始我怀疑是游戏版本问题，于是在网上找了该游戏的各种不同版本，逐一试玩后发现结果还是一样。

### Aha! moment

这个问题一直困扰了我相当长的一段时间，期间我曾经多次尝试在Google上对此问题进行搜索，试图找到问题的原因，比如搜索“空洞骑士 switch 为什么 9999”、“switch hollow knight 99999”等，全都一无所获，仿佛互联网上并没有其他人遇到过类似的问题。

所以问题到底出在哪呢？

就在我几近放弃的时候，我想到了一个可以cut the knot的笨办法。甭管游戏是否被修改过，就算它现在真的开了cheat，那我能否手动将cheat给关掉呢？这样游戏应该就能正常玩了吧。

带着这个想法，我开始搜索并尝试在switch上安装开关cheat的相关工具。

### 试验

我想到之前有看到过一个cheat插件以及能在游戏界面中实时开关cheat的overlay工具。简单搜索后我找到了[Tesla overlay](https://gbatemp.net/threads/tesla-the-nintendo-switch-overlay-menu.557362/)和[Edizon](https://github.com/WerWolv/EdiZon)（switch存档和cheat管理工具）。

在安装Edizon cheat overlay的过程中，我注意到网上[教程](https://www.cfwaifu.com/edizon-cheats/)中的这么一句话：

> By default, Atmosphere enables all cheats that can be found on your SD when launching a game. This can be changed via Atmosphere’s configuration files.

原来，大气层默认会在启动游戏时打开所有找到的cheats。这似乎也印证了我之前的猜测：我的switch上的某些空洞骑士的cheats somehow被打开了。

在安装试用的过程中还发生了2个小插曲：

一开始，在按照教程安装好Tesla overlay和Edizon并重启了switch之后，我进入游戏尝试通过快捷键（hold down `L` and `DPad Down` and push on the `right joy stick`）打开overlay，结果每次只要一进入Edizon overlay菜单switch就会crash。简单Google搜索后发现，原来是Edizon早已停更，当前的版本并不支持最新版系统固件，需要下载安装新版的[Edizon-SE](https://github.com/tomvita/EdiZon-SE)和[Edizon-Overlay](https://github.com/proferabg/EdiZon-Overlay)。

此后，我还在新版Edizon-SE的[README](https://github.com/tomvita/EdiZon-SE?tab=readme-ov-file#how-to-install)里注意到，原来不光需要按前面教程中说的修改配置文件的默认值，还需要将那一行配置项前面的";"注释符号删除，否则修改结果并不会生效。

> For the best experience, open the /atmosphere/system_settings.ini file and change dmnt_cheats_enabled_by_default = u8!0x1 to dmnt_cheats_enabled_by_default = u8!0x0. If the file does not exist you can copy the template from /atmosphere/config_templates/system_settings.ini and change the line, **remember to remove the ";" in front**.

### 成果

在下载并重新安装新版的Edizon-SE和Edizon-Overlay以及修改配置文件确保所有cheats默认关闭之后，我再次打开游戏，这次终于可以正常进入Edizon overlay界面了，并且可以看到所有cheats都是关闭状态。

![2025-05-28 19.19.16.jpg]({{site.baseurl}}/assets/images/2025-05-28 19.19.16.jpg)

原来一直困扰我的就是上图中这个罪恶的"Geo 999999"和其他的空洞骑士的cheats。

![2025-05-28 19.19.38.jpg]({{site.baseurl}}/assets/images/2025-05-28 19.19.38.jpg)

我简单尝试打了两个小怪，发现游戏终于正常了（只有3个吉欧，而不是一开局就有99999个）。

### 复盘

回想我最初遇到的“空洞骑士99999个吉欧”的问题，原因应该就是大气层默认打开了设备上所有找到的cheats，而我的switch上不知为何会有空洞骑士的cheats，于是每次进入游戏就会有99999个吉欧和无限生命。这么一想，我记得之前曾经有一次尝试安装过Tesla overlay和Edizon，后来放弃使用overlay之后便忘记了，可能过程中无意进行了某些cheat相关的操作，但也无从得知了。

### 题外话

在了解了问题的原因之后，我再次在Google，Brave和DuckDuckGo等搜索引擎上对此问题进行搜索，搜索词为“switch hollow knight geo 99999"，结果这些搜索引擎中只有DuckDuckGo的第一条返回结果是Edizon cheats for switch hollow knight (including geo 99999)，与我的描述高度吻合。而Google和其他搜索引擎的首页结果均无任何跟cheat有关的结果。这让我不禁怀疑这些商业搜索引擎对搜索结果进行了过滤。试想如果当初我是用的DuckDuckGo来搜索这一问题的话，会不会更早找到正确结果呢？

想到这里，我果断决定以后弃用Google，改用DuckDuckGo。
