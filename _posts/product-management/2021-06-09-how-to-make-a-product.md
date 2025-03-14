---
published: true
title: 如何打造一款产品
category: product-management
tags: innovation
---

- TOC
  {:toc}

## 前言

程序员出身的我，曾经以为打造一款产品是这样一个过程：

某一天洗澡或者散步时突然脑中蹦出一个点子，想到可以使用某种技术来满足某个（自己的）需求，比如每天早晨可以将新闻发送到 Kindle 上阅读（[news2kindle](https://github.com/goooooouwa/news2kindle)），于是立即埋头着手设计界面，紧接着吭哧吭哧地敲代码，在熬夜并且喝了太多咖啡之后，终于在某天凌晨将产品部署上线了。

然而，几个月之后，面对无人关注的 Github 项目首页和每月如期而至的云服务账单，已经逐渐失去当初那股冲劲儿的自己会回想起过去几年里曾经不止一次发生过的类似经历。不禁感叹：

- 为什么我的产品总是失败了？
- 打造一款产品到底是怎么一回事？
- 怎样才能打造出成功的产品？

如果你对这些问题也抱有同样的困惑，希望本文能给你一些启发。本文主要会介绍以下产品相关的理论，包括：

1. 产品的定义和分类
2. 产品的构成
3. 打造产品的不同阶段
4. 各阶段的具体活动

由于产品管理所涉及的话题十分广泛，很难通过一篇文章进行全面深入的探讨，因此本文仅会对每个话题进行较为简要的介绍，旨在为对“如何打造产品”感兴趣的小伙伴提供一个产品管理全生命周期的入门引导。

题外话：在你眼中打造一款产品是一个怎样的过程？欢迎留言分享。

## 何为产品

在我们讨论如何打造产品之前，有必要先弄清一个问题：产品到底是什么？

百度百科上对产品的定义是：

> 产品是指作为商品提供给市场 ，被人们使用和消费，并能满足人们某种需求的任何东西，包括有形的物品、无形的服务、组织、观念或它们的组合。

这里面有两点值得注意：

- 产品是一种商品
- 产品要能满足人们的需求

这两点分别体现了产品的商业价值和用户价值，即产品是需要盈利的，还要能解决用户问题。盈利才能平衡开支和做新投资，而只有解决用户问题才会有人愿意买单。一个产品只有能同时满足这两点才能在市场上存活下去。

### 产品的分类

大家日常生活中随处可见各式各样的产品和服务，比如，床、鞋子、袜子、牙刷等，而服务通常是无形的，比如，理发、洗车、家政维修等，还有些企业经营的是产品和服务的组合，比如餐厅会同时提供产品（食物）和服务（就餐环境）。

此外，还有很多产品和服务是大家平时生活中很少接触到的，通常是面向企业的产品和服务，比如：客户关系管理、财务管理、库存管理、办公自动化等。

产品有很多种分类方式，有形的还是无形的，面向消费者的（to C）还是面向企业的（to B），一种比较完善的产品分类是国家统计用产品分类，涵盖了几乎所有类型的产品和服务。比如：

1. 农业产品
2. 林业产品
3. 饲养动物及其产品
4. 渔业产品
5. 农、林、牧、渔服务
6. 煤炭采选产品
7. 石油和天然气开采产品

完整分类请见[统计用产品分类目录](http://www.stats.gov.cn/tjsj/tjbz/tjypflml/)。

近些年随着互联网的高速发展，各种各样的软件产品和服务也层出不穷，深入到人们生活的方方面面。为了区分这些软件和服务，我们可以将它们进一步细分。比如，苹果 App Store 将其中的软件划分为许多不同的类别，比如：

- 摄影与录像
- 儿童
- 娱乐
- 购物
- 健康健美
- 教育
- 旅游
- 美食佳饮
- 商务
- 社交
- 游戏

完整分类请见[苹果应用分类](https://developer.apple.com/cn/app-store/categories/)。

## 产品的构成

想要打造一款产品，我们势必得先知道一款产品是有哪些部分组成的。为了对此获得比较全面的认识，让我们分别从产品的消费者和产品的创造者（设计师和产品经理）的不同视角来了解一款产品的构成。

### 消费者眼中的产品构成

当我们作为消费者在选购一款产品时，一般能比较直观地了解到它的品牌、外观、功能和售价，比较细心的买家可能还会去了解该产品的质量、技术规格和服务保障等。如果我们希望把这些产品属性进行一个划分，一种经典的划分方法是科特勒 1988 年提出的产品三层次理论。

#### 产品的三层次理论

产品的三层次理论认为，产品是由以下三个层次组成：

- 核心产品（Core Product）。核心产品是产品的灵魂，是指产品的有用性，是产品的使用价值或效用，是消费者真正购买或使用该产品的动因。
- 有形产品（Actual Product）。有形产品是核心产品的具体表现形式，是整个产品内涵的有形载体，是一种看得见摸得着的产品层次，是消费者视角的产品。
- 附加产品（Augmented Product）。附加产品即附加服务或利益，是指卖方能提供消费者在实体商品之外更多的服务与利益，例如：免费安装、检修服务等。

![产品的三层次理论](https://goooooouwa.eu.org:8143/static/images/20210531175345.png)

三层次理论通过体现消费者需求的多层面性，解释了消费需求的动机，同时很好地展示了消费者视角中产品的整体概念。

此外，1994 年科特勒又将三层次结构扩展成五层次结构，称为五层次理论，即包括核心产品（Core Benefit）、一般产品（Generic Product）、期望产品（Expected Product）、附加产品（Augmented Product）和潜在产品（Potential Product）。具体含义可以参考这篇：[产品概念之 3/4：五层次理论 —— 消费者体验视角的产品概念](https://blog.csdn.net/zhanglinneu/article/details/85105389)。

当然，想要打造一款产品，仅仅从消费者眼中了解产品是不够的，我们有必要了解在产品创造者眼中产品是怎样的构成。

### 设计师眼中的产品构成

与直觉的理解不同，设计师眼中的产品并不仅仅只是视觉效果和交互行为，所有这些表层的内容和功能都有它背后所服务的用户需求和产品目标。

《用户体验要素》中将产品的用户体验设计划分为了五个不同层面，从下到上依次为：

1. 战略层，主要包括用户需求、产品目标。
2. 范围层，主要包括功能规格、内容需求。
3. 结构层，主要包括交互设计、信息架构设计。
4. 架构层，主要包括界面设计、导航设计、信息设计。
5. 表现层，主要包括视觉设计。

这五个层面中的每一层都是基于下面的一层所决定的，每一层之间还存在一个由抽象到具体以及大体上的时间先后顺序。

![用户体验要素的五层模型](https://goooooouwa.eu.org:8143/static/images/20210531085702.jpeg)

除了功能特性和用户体验，打造一款产品还需要考虑许多方面，这些通常是产品经理的工作。因此接下来让我们来看看产品经理眼中的产品是如何构成的。

### 产品经理眼中的产品构成

先引用一段对产品经理职位的介绍：

> 产品经理（Product Manager）是企业中专门负责产品管理的职位，产品经理负责市场调查并根据用户的需求，确定开发何种产品，选择何种技术、商业模式等，并推动相应产品的开发组织。他还要根据产品的生命周期，协调研发、营销、运营等，确定和组织实施相应的产品策略，以及其他一系列相关的产品管理活动。

可以看到，为了确保打造的产品最终能真正地满足目标用户的需求并在市场上获得符合预期的盈利，产品经理需要参与到产品的整个生命周期中去。

我自己喜欢用下面这张图来帮助自己理解产品经理眼中产品的构成。

![产品经理眼中的产品构成](https://goooooouwa.eu.org:8143/static/images/20210609164857.png)

在本文后面的内容中，我们会从产品经理的视角出发，一起来了解打造一款产品的不同阶段的具体活动。

## 打造产品的不同阶段

《产品经理装备书》中给出的产品管理的生命周期图很好的展示了打造一款产品需要经历的四大主要阶段：

1. 发现与创新：包括市场洞察和战略制定。
2. 新产品计划：包括产品概念、可行性评估和产品定义。
3. 新产品导入：包括产品的开发和上市。
4. 上市后的产品管理：包括产品运营和绩效管理。

![产品管理的生命周期](https://goooooouwa.eu.org:8143/static/images/20210609155312.jpeg)

接下来让我们来具体了解一下打造产品的这四个阶段具体会进行哪些活动。

## 一、市场研究与洞察

在进行任何形式的产品设计之前，我们首先必须弄清楚：产品需要解决的是什么问题？它的目标用户是谁？它将如何盈利？

为了回答这些问题，我们需要对产品所在市场进行全面的研究以获得产品市场机会的相关洞察。

### 市场研究与趋势预测

市场研究一般包括市场宏观环境分析、行业竞争分析和企业竞争力分析。进行这些分析的前提是获得所需的相关信息，因此让我们首先了解该如何建立自己的信息收集体系。

#### 建立信息收集体系

在如今海量信息的互联网时代，为了对市场进行系统的研究和预测，我们该如何有效地收集市场信息呢？《商业预测》中给出了一种四级分类的信息收集体系，依次是“全球>国家>行业>企业”。该框架为我们收集市场信息提供了四个分明的层次，这有助于我们理解不同层次信息间的联系，并以此建立大局观。

这些信息的一些重要的来源包括：

1. 全球
   - 联合国，网站是[www.un.org](www.un.org)
   - 联合国的各署，比较重要的是[联合国开发计划署（UNDP）](https://www.un.org/zh/aboutun/structure/undp/)
   - [世界银行](https://data.worldbank.org.cn/)，了解国际金融政策变化
   - [国际货币基金组织](https://www.imf.org/zh/Home)，了解货币汇率和各国贸易情况
   - 国际上的各种经济组织，比如[WTO 世界贸易组织](https://www.wto.org/)
2. 国家
   - 各国部委，比如，在美国财政部网站上，可以查询美国联邦政府的财税政策以及相关数据
   - 各国央行，了解国家的货币政策以及金融政策
   - 各国顶尖高校和研究机构，了解该国在某一领域的科技竞争力
3. 行业
   - 各国股市，了解行业和企业的表现
   - 行业协会或展会，比如，一年一度的 CES 国际消费类电子产品展
   - 行业聚集地，比如，美国互联网企业聚集的硅谷地区
   - 行业媒体，比如[Gartner](https://www.gartner.com/cn)和[IDC](https://www.idc.com/cn)等行业媒体的研究报告和数据
4. 企业
   - 行业领军企业，比如目前人工智能领域的领军企业谷歌
   - 边缘创新企业，比如太空探索方面的企业 SpaceX
   - 关键人，比如，在电动汽车、太阳能城市和太空探索等多个领域都有建树的埃隆·马斯克

#### 行业宏观环境分析

在进入任何一个行业之前，我们需要对行业的整体情况获得一个比较全面的认识，以确定企业是否在该行业具有竞争力，以及该如何应对行业未来可能的变化。为此我们需要对目标行业进行宏观环境的分析，一种有效工具就是 PESTEL 分析模型。该模型包括六大方面的因素分析：

1. 政治因素(Political)
2. 经济因素(Economic)
3. 社会因素(Social)
4. 技术因素(Technological)
5. 环境因素(Environmental)
6. 法律因素(Legal)

通过对行业的这六大方面的影响因素进行分析，我们可以识别出外部环境中对行业以及企业自身有冲击性影响的不同力量，这将有助于我们做出更符合行业发展的产品规划。

有了对行业的宏观了解，下一步让我们来了解一下该行业的整体竞争状况。

#### 行业竞争分析

迈克尔·波特提出的波特五力分析模型被广泛的应用于行业竞争分析，它主要关注的五大力量包括：

1. 供应商的议价能力（Bargaining Power of Suppliers）
2. 购买者的议价能力（Bargaining Power of Buyers）
3. 新进入者的威胁（Threat of New Entrants）
4. 替代品的威胁 （Substitutes）
5. 同业竞争者的竞争程度（Rivalry）

![波特五力分析图](https://goooooouwa.eu.org:8143/static/images/20210605165442.png)

在对行业的整体竞争状况进行分析之后，我们还必须弄清：企业自身在市场上的竞争力如何？分别有哪些优势和劣势？这就需要我们对企业进行竞争力分析。

#### 企业竞争力分析

想了解一个企业自身的竞争力，我们可以使用 SWOT 分析模型。它是一种将企业内外部条件和行业环境各方面内容进行综合分析的一种方法。主要包括内部优势和劣势，以及外部的机会和威胁。

![SWOT分析图](https://goooooouwa.eu.org:8143/static/images/20210601170843.png)

除了对行业当下的情况进行分析，我们还有必要对行业未来几年的发展趋势进行预测，这样才能更好的发现市场机会并为市场变化做好提前准备。

#### 行业趋势预测

《商业预测》中介绍了一种分析行业趋势的工具，叫作连锁反应图。该工具通过对七种信号的识别以及信号背后的五大驱动力的分析，结合多轮的连锁反应分析，以预测行业未来几年的发展走势。

基于连锁反应图进行趋势分析的三大步骤是：

1. 发现信号，比如新产品、新做法、新的市场策略、新政策、新技术、新现象和新组织
2. 分析驱动力，包括政治、经济、社会、技术和环境驱动力
3. 连锁反应分析，基于驱动力推演出一级、二级、三级连锁反应

![连锁反应图](https://goooooouwa.eu.org:8143/static/images/20210605172504.jpg)

### 市场细分与目标市场选择

目前我们已经对市场宏观环境、企业竞争力以及行业的整体发展趋势得到了一定的了解，下一步就需要确定产品的目标市场，这么做一方面是为了确定产品所服务的目标用户，更重要的是，产品能从哪些市场细分中盈利。

#### 细分市场的划分

为了找到适合企业的目标市场，我们可以对市场进行细分，市场细分可用的划分维度有很多，主要包括：

- 地理细分，包括国家、省、市、区、乡镇和社区等
- 人口统计细分，包括：
  - 年龄和生命周期阶段，比如，0 ～ 5 个月的新生婴儿
  - 生活阶段，比如结婚、买房、赡养老人等
  - 性别，比如男性、女性和其他性别
  - 收入，比如特定收入水平的人群
  - 世代，比如 Y 世代、Z 世代等
  - 种族和文化，比如亚洲人、美国黑人等
- 心理统计细分，比如 VALS 细分模型按照动机和资源将消费者分为 8 种心理群体：创新者、思考者、成就者、体验者、信仰者、奋斗者、生产者、幸存者
- 行为细分
  - 决策角色， 人们在一个购物决策中扮演五种角色：发起者、影响者、决定者、购买者、使用者
  - 使用者和使用情况，比如：使用场合、使用者状况、使用频率
  - 购买者准备阶段，包括：知晓、曾经尝试、最近尝试、轻度使用者、经常使用者、重度使用者

#### 细分市场的评估和选择

在对市场进行细分后，我们需要对不同的细分市场进行评估。在评估这些细分市场时，主要需要考虑两个方面的因素：

1. 该细分市场的吸引力，比如该市场的规模、成长性、盈利性、风险程度
2. 企业的目标和资源在该细分市场下的表现，比如该市场是否符合企业长期目标，企业是否具有该市场所需的必要竞争力

为了了解细分市场的潜在规模，我们可以对该市场的潜量进行估算，通常可以采用两种估算方法：市场累加法（market-buildup method）和购买力指数法（Buying-power index method）。

##### 市场累加法

市场累加法，是指先识别某一地区市场的所有潜在顾客并估计每个潜在顾客的购买量，然后计算得出该地区市场需求。当企业掌握左右潜在买主的名单以及每个人可能购买产品的估计量时，则可直接应用市场累加法。

例如，某一地区淡啤酒需求 = 该地区人口数 x 人均可支配收入中用于食品支出的平均金额 x 食品支出中用于饮料支出的平均百分比 x 饮料支出中用于含酒精饮料支出的平均百分比 x 含酒精饮料支出中用于啤酒支出的平均百分比 x 啤酒饮料支出中用于淡啤酒支出的预期百分比。

##### 购买力指数法

购买力指数法也称“多因素指数法”，是指借助与区域购买力有关的各种指数(如区域购买力占全国总购买力的百分比，该区域个人可支配收入占全国的百分比，该区域零售额占全国的百分比，以及居住在该区域的人口占全国的百分比等)来估计其市场潜量的方法。

在综合考虑市场和企业自身特点后，我们将会选出产品需要进入的目标市场。

### 小结

在市场研究与洞察阶段，我们了解了如何对企业所在的行业进行宏观环境和竞争力分析，以及如何对行业趋势进行预测，并且根据市场细分的吸引力和企业自身特点对目标市场进行了评估和选择，至此我们已经对新产品所要进入的市场有了比较全面的认识，这将为我们下一阶段对产品的探索和定义起到指导性作用。

## 二、产品探索与定义

在对市场进行了深入的研究之后，我们明确了新产品所要进入的目标市场，接下来就需要对产品概念进行探索和定义了。在这一阶段我们会探索多种不同的产品概念，并对这些概念进行用户测试和可行性验证，以确保产品能够满足目标用户的需求并在市场上获得符合预期的盈利。最后我们会为成熟的产品概念给出明确的产品定义，为下一阶段的产品研发做好准备。

### 产品探索

#### 好的产品点子从哪里来？

> “The best way to have a good idea is to have lots of ideas.”
> ― Linus Pauling

莱纳斯·鲍林曾经说过：得出好点子的最好办法就是先得出很多点子。其中大多数的点子可能都行不通，我们需要学会抛弃那些不适合的。

新产品点子的来源有多种，包括深入的市场分析、对生活的细心观察，甚至是结构化的思维活动，我们需要做的就是鼓励来自各种不同视角的想法。与具有不同领域背景的角色一起进行头脑风暴是一种很好的催生产品点子的方法。

![头脑风暴](https://goooooouwa.eu.org:8143/static/images/20210531085307.jpg)

#### 产品探索的流程

想法总是比可用资源多，不是所有的想法都有足够的资源去实现商业化。结构化的流程有助于有效、快速地缩小目标范围。设计思维为产品创新提供了一个很好的流程框架，它将创新过程大体分为五个阶段：

1. 共情：理解所涉及的人的需求；
2. 确定问题：以人为中心的方式重新组织和定义问题；
3. 形成概念：在创意阶段中创造出许多想法；
4. 原型设计：制定问题的原型/解决方案；
5. 测试：不断与目标用户测试原型。

![设计思维流程图](https://goooooouwa.eu.org:8143/static/images/20210605225637.jpeg)

在对产品概念进行多轮迭代之后，我们将得出几种能潜在解决用户问题的产品概念。当然，除了解决用户问题，产品还需要能从中盈利，因此我们还需要对产品的商业层面进行探索，其中包括产品的市场定位、商业模式和价值主张。

#### 市场定位

在为产品选定了目标细分市场之后，为了该产品能在市场上具有不可取代的市场地位，我们需要为该产品找到其差异化的市场定位。

我们可以依据以下四点原则选择产品的市场定位：

1. 根据具体的产品特点定位
2. 根据特定的使用场合及用途定位
3. 根据顾客得到的利益定位
4. 根据使用者类型定位

最终通过寻找一个或者多个差异化的竞争力，我们能为该产品找到其独特的市场定位。

#### 商业模式与价值主张

正如前面所说，任何一款产品都是需要盈利的，因此我们需要为我们的产品思考它能为客户带来怎么样的价值，以及我们应该采用怎样的商业模式。

为了更直观地理解和设计产品的商业模式，我们可以使用商业模式画布来进行分析。商业模式画布将商业的四个主要方面“客户、产品、基础设施、财务生存能力”分解为九个基本模块：

1. 客户细分：企业想要接触和服务的不同人群和组织。
2. 价值主张：为特定细分客户创造价值的系列产品和服务。
3. 渠道通路：如何沟通，接触其细分客户而传递其价值主张。
4. 客户关系：与特定细分客户群体建立的关系类型。
5. 收入来源：从每个客户群体获取的现金收入（需要从创收中扣除成本）。
6. 核心资源：让商业模式运转所必需的最重要因素。
7. 关键业务：为了确保商业模式可行，企业必须做的最重要的事情。
8. 重要伙伴：让商业模式运转所需的供应商和合作伙伴的网络。
9. 成本结构：运营一个商业模式所引发的所有成本。

![商业模式画布](https://goooooouwa.eu.org:8143/static/images/20210525064447.jpg)

为该产品找到符合其自身定位和目标市场的商业模式，我们需要对产品的九个基本模块进行充分的思考和设计，在此之前不妨了解一下以下典型的商业模式式样：

- 非绑定式商业模式
- 长尾式商业模式
- 多边平台式商业模式
- 免费式商业模式
- 开放式商业模式

商业模式中最核心的就是价值主张，即该产品可以为客户带来哪些独特的价值，常见的价值主张包括：

- 新颖（Newness）
- 性能（Performance）
- 设计（Design）
- 品牌/身份地位（Brand/Status）
- 价格（Price）
- 成本削减（Cost reduction）
- 风险抑制（Risk reduction）
- 可达性（Accessibility）
- 便利性/可用性（Convenience/usability）

至此我们已经探索了该产品概念的原型设计、市场定位和商业模式，在将产品概念投入研发之前，我们还需要对这些概念进行可行性评估，以确保该产品是值得进行投资的。

### 可行性评估

在进行实际的产品研发之前，为了确保企业对该产品的投资能得到符合预期水平的收益，我们需要对产品概念进行验证，评估其商业可行性。为此我们需要回答几个方面的问题，比如：

- 产品能取得多少市场份额？潜在的收入有多少？何时能达到盈亏平衡点？
- 企业是否有能力研发、运营该产品？
- 产品的研发、生产和运营需要投入多少成本？

为了对这些方面进行有效的评估，我们需要与企业的不同职能角色紧密合作，评估产品研发、上市和运营所需的财务成本、人力资源支持，并初步制定各职能的支持计划，比如营销计划、上市计划等。

在对产品可行性进行评估之后，我们便可以对产品是否值得投资做出一个基本判断。如果企业决定要将该产品概念投入研发，我们便需要为该产品进行更加明确的定义和设计。

### 产品定义

在进行正式的产品研发之前，为了让研发团队对所需开发的产品得到准确的理解，我们需要给出明确的产品定义，包括：

- 产品的目标市场和用户
- 产品的定位和商业模式
- 产品的用户需求和场景
- 产品的功能和原型设计
- 产品的发展规划（Roadmap）

有些企业会通过正式的市场需求文档（MRD）和产品需求文档（PRD）来传达这些信息（比如这份[行程规划旅游 APP—市场需求文档（MRD）](http://www.woshipm.com/evaluating/921572.html)），有些则采用更轻量级的方式（比如需求列表）来管理。总之，有了这些说明性的产品文档的支持，在产品的研发阶段我们便可以有效地与设计和开发人员沟通产品的需求。

### 小结

在产品探索与定义阶段，我们了解了产品探索的基本流程，以及如何设计产品的市场定位、商业模式与价值主张。为了确保产品的商业可行性，我们还对其进行了可行性评估。此后，为了产品能顺利的进入研发，我们还为产品给出了明确的定义。

至此产品的探索阶段便已完成，接下来就需要进行产品的实际研发和上市准备了。

## 三、产品研发与上市

产品研发与上市阶段的重点是按照既定的产品方案来进行实际的产品开发，大部分具体的设计、开发和测试工作都会在这一阶段进行。同时，这一阶段还需要着手生产、市场营销以及支援体系方面的一些上市前的准备工作，包括生产工艺的开发、产品的上市计划以及服务人员培训等。

### 产品研发

产品研发阶段，产品经理负责确保产品是根据产品需求开发的，并且保证产品在按时、按预算且高质量地生产出来。主要的工作包括：

- 规划排期：根据产品发展规划制定阶段性的发布计划，对产品需求进行排期
- 研发配合：与研发团队沟通需求，同时根据反馈，调整、修正产品方案中的不足
- 测试验收：根据产品需求，校验研发交付的成果，给出调整、改进意见和方案

### 产品上市规划

为了产品的顺利上市，我们需要协调和同步许多跨职能部门的上线前的相关准备，包括生产计划的制定、营销策略的制定、销售和服务人员培训等。

#### 产品生产计划

生产部门会根据产品的上市安排和需求预测来制定相应的生产计划，主要包括四个部分：

- 综合生产计划：对企业未来较长一段时间内资源和需求之间的平衡所做的概括性设想。
- 主生产计划：确定每一具体的最终产品在每一具体时间段内的生产数量。
- 物料需求计划：确保规定的最终产品所需的全部物料(如原材料、零件和部件等)以及其他资源在需要的时候能供应上。
- 作业进度计划：具体的生产实施计划，比如确定订单的加工顺序；确定机器加工每个工件的开始和完成时间。

#### 产品营销策略

市场营销部门会根据产品的市场定位对产品的营销组合进行策略的制定，传统的市场营销组合（4P）包括四大方面：

- 促销策略：包括销售促进、广告、人员推销、公共关系、直销等。
- 产品策略：包括产品的种类、质量、设计、特性、品牌名称、包装、规格、服务、保证、退货等。
- 渠道策略：包括销售渠道、覆盖区域、产品分类、场所、库存管理、物流运输等。
- 价格策略：包括产品的目录价格、折扣、津贴、付款期限、信用条件等。

#### 相关人员培训

为了能让客户获得优质的产品配套服务，我们还需要协助企业的培训部门对相关人员进行产品培训，其中包括销售人员、客服人员、维修人员以及经销商等。

### 小结

在产品研发和上市阶段，我们了解了产品经理如何参与到产品的研发过程中，以及如何与跨职能部门协调同步，以做好各方面上线前的准备工作。

至此产品的前期准备工作便已基本完成，接下来就要进入真正决定成败的产品运营与演进阶段了。

## 四、产品运营与演进

产品的成功上市并不意味着打造产品的工作就此完成，毕竟到目前为止产品还未获得任何盈利。从下面这张典型的产品现金流曲线图我们可以看到，一款产品往往在其上市后的一段时间里都是处于亏损的状态。而一款产品能否在其上市后的生命周期里转亏为盈，与产品的运营是有着密不可分的关系的。

![产品的现金流曲线](https://goooooouwa.eu.org:8143/static/images/20210608161052.png)

### 产品运营

所谓产品运营，是指基于企业经营和产品战略，以最优的路径和最高效的执行，建立产品在市场上的竞争优势，并最终取得产品市场成功的过程。

产品运营的工作主要包括：运营策划、商务拓展、媒介、活动、数据分析、市场监控。

1. 运营策划：主要是以数据为依据的产品运营方案策划。

2. 商务拓展（BD）：运营会接触到不同渠道的转化效率，因此相对的需要和渠道商打交道或者公司内部的销售人员接触。

3. 媒介：包括了文案的撰写、话题策划、文章发布等。

4. 活动营销：结合产品推广或是品牌宣传，策划活动营销方案并有力执行之，促使达到提高产品和品牌知名度的目的。以及活动的用户调研，奖励等。

5. 数据分析：数据决定运营的执行。

6. 市场监控：主要是战略层面，包括：行业市场的监控以及竞争对手的监控。

### 运营体系的搭建

前面提到的所有运营工作，背后是有着完整的逻辑的，即所谓的运营体系。运营体系的本质是一个层层筛选的流量变现漏斗，帮助企业获得客户增长以源源不断地创造效益。AARRR 漏斗模型可以很好地帮助我们理解获客和维护客户的原理。

![AARRR模型](https://goooooouwa.eu.org:8143/static/images/20210606223459.png)

构建运营体系我们可以从三个层面去着手：

1. 界定用户关键行为，即寻找用户成长的转折点。
2. 制定用户运营策略，包括新手引导、用户成长体系和流失用户召回。
3. 增长策略，包括产品化的增长策略和外部增长策略。

### 产品的演进

产品上线后，一方面我们需要持续地优化运营体系，更高效地服务更多的客户并为企业创造更多收益；另一方面，为了延续产品长期的市场竞争力，我们需要同时着手打造新一代的产品，以确保在当前产品到达它的衰退期或者在市场上的表现低于预期时，能及时将新一代的产品推向市场。

除了推出新一代的产品，结合产品的市场表现以及市场本身的成熟程度，企业还可以通过拓展产品线乃至推出子品牌的方式演进产品，甚至有的时候需要通过重新调整产品方向来争取更多市场份额。

### 小结

在产品的运营与演进阶段，我们了解了如何搭建运营体系以及产品未来还有哪些可能的演进方向。可以看出，产品管理的工作实际上是没有结束之说的，因为产品只有不断的演进以适应市场和用户需求的变化才有可能保持长期的生命力。

## 结语

至此我们便对打造一款产品所需经历的四大阶段及其相应的一系列活动进行了整体的介绍，希望对此话题感兴趣的小伙伴能有所收获。

本文更多的还是从广度出发试图对产品管理的全生命周期进行一个完整的介绍，由于篇幅有限，并未对特定的活动进行深入的探讨，不免会担心整体内容流于表面。笔者计划下次基于具体的产品命题来进行一次实际的上手演练，以作为本文的补充，希望通过理论与实践相结合的方式让这个话题更加落地。

本文是否有回答你心中关于“如何打造一款产品”的问题？欢迎留言反馈。

## 参考

- 《[产品经理装备书](https://book.douban.com/subject/27067499/)》
- 《[营销管理](https://book.douban.com/subject/10568352/)》
- 《[商业模式新生代](https://book.douban.com/subject/6718487/)》
- 《[用户体验要素](https://book.douban.com/subject/6523997/)》
- 《[商业预测](https://book.douban.com/subject/27171485/)》
- [产品概念之 2/4：三层次理论 —— 生产者主导视角的产品概念](https://blog.csdn.net/zhanglinneu/article/details/85104567)
- [产品概念之 3/4：五层次理论 —— 消费者体验视角的产品概念](https://blog.csdn.net/zhanglinneu/article/details/85105389)
- [10 个案例说明什么是产品模型（2）](http://www.chanpin100.com/article/43594)
- [“用户体验要素”的 5 层模型](https://zhuanlan.zhihu.com/p/106062450)
- [PESTEL 分析模型](https://wiki.mbalib.com/wiki/PESTEL%E5%88%86%E6%9E%90%E6%A8%A1%E5%9E%8B)
- [波特五力分析模型](https://wiki.mbalib.com/wiki/%E6%B3%A2%E7%89%B9%E4%BA%94%E5%8A%9B%E5%88%86%E6%9E%90%E6%A8%A1%E5%9E%8B)
- [你眼中的产品经理是什么？](https://zhuanlan.zhihu.com/p/32532992)
- [设计思维过程中的 5 个阶段](http://www.woshipm.com/pd/988909.html)
- [市场定位](https://baike.baidu.com/item/%E5%B8%82%E5%9C%BA%E5%AE%9A%E4%BD%8D)
- [新产品从开发到上市的阶段流程](https://www.cnitpm.com/pm/1091.html)
- [行程规划旅游 APP—市场需求文档（MRD）](http://www.woshipm.com/evaluating/921572.html)
- [如何构建运营体系？](http://www.woshipm.com/operate/1645278.html)
- [产品运营](https://wiki.mbalib.com/wiki/%E4%BA%A7%E5%93%81%E8%BF%90%E8%90%A5)
- [说说产品经理各个阶段的工作内容（一）](https://zhuanlan.zhihu.com/p/24430022)
- [工作计划：如何制定生产计划](https://www.glzzj.com/7663.html)
- [新产品上市计划书](https://doc.mbalib.com/view/847bd33d1efd1a7f3c36a48261982d97.html)
