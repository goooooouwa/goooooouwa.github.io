---
published: true
title: GoPlan Web版v1.0正式上线
category: side_project
tags: todo project_management life product
---

## TL'DR

经过两个多月的熬夜肝代码，今天 GoPlan Web 版 v1.0 正式上线！即刻体验：[https://goooooouwa.fun:8095/welcome](https://goooooouwa.fun:8095/welcome)

### 如何获得帮助

#### 在线客服

使用中如果遇到任何问题欢迎点击页面右下角的“客服”按钮咨询在线客服（即作者[本人]({% link about.md %})）。

#### 提交 Bug

如果认为自己遇到了产品的 bug，欢迎在 Github 提 issue（[地址](https://github.com/goooooouwa/goplan-web/issues))。

# GoPlan: 助您如期达成目标

GoPlan 是一款旨在助您达成目标的应用。有了它，您可以轻松地将你的目标拆分成一系列可执行的任务，并且随时利用多种直观的时间线轻松管理任务计划。

![产品截图](https://goooooouwa.fun:8143/static/images/202208090949907.png)

[立即使用 GoPlan](https://goooooouwa.fun:8095/welcome)，告别永远处理不完的待办事项，让一起尽在计划之中。

## 目标人群和使用场景

### 目标人群

生活中对做计划有需求的个体，比如职场人士、学生等。

### 使用场景包括但不限于：

- 学会一门外语/编程/弹钢琴
- 换一份新的工作
- 考研/考证
- 装修新房

## 功能特色

### 核心功能

- [x] 轻松关联依赖任务
- [x] 具有年度/季度/月以及周视图的任务时间线
- [x] 根据任务依赖关系自动更新时间计划，轻松了解是否如期达成目标
- [x] 自动推迟到期未完成的任务

### 其他功能：

- [x] 支持创建子任务
- [x] 多种颜色区分的任务时间线
- [x] 支持手机平板访问
- [x] 无需注册即可体验（不支持自动计划和推迟任务）
- [x] 支持 Google & GitHub 账号登录
- [x] 在线客服
- [x] 支持中英文

### 未来开发计划

- [ ] 原生安卓 app
- [ ] Web 端和服务端优化

## 技术实现（Specs for nerds）

### 代码库（开源）

- GoPlan Web: [https://github.com/goooooouwa/goplan-web](https://github.com/goooooouwa/goplan-web)
- GoPlan API: [https://github.com/goooooouwa/goplan-api](https://github.com/goooooouwa/goplan-api)

### 技术栈

![](https://goooooouwa.fun:8143/static/images/202208091134111.jpg)

- 前端 Web 框架: React with Node.js
- 前端 UI 组件库: Metarial UI
- 后端 Web 框架: Rails
- 运行环境: Docker
- 数据库: PostgreSQL
- 静态文件服务器 & 反向代理: Nginx
- 编程语言: JavaScript, Ruby
- 安全性: OAuth 2, HTTPS

### 当前服务器配置

- 1 个树莓派 3B+
- 64GB SD 卡
- 电信家庭网络

初期用户数不多的话，树莓派的 4 核 1G 的配置应该也够了，如果用户访问量大到服务器崩溃了，会考虑升级配置。

## 背后的思考

传统的 todo 任务工具对任务的管理粒度太细，常常只见树叶不见森林，难以做长远计划。有些任务工具（例如 Any.do）虽然会提供日历视图，但还是落脚于每一天的安排，无法看到一年或者一个季度的整体安排。另一方面，有一些项目管理的工具虽然提供了很方便的计划功能（例如 Google Sheet 手动创建 Gantt 图），但是更新和维护计划非常困难，需要手动调整每个受影响的任务时间安排。

而 GoPlan 则结合了任务管理和项目计划工具两者的优点，既能方便地创建和调整长远的任务计划，又能轻松地将计划落实到每天的具体工作安排，从计划到落地执行，全程支持用户实现个人目标。

个人一直以来希望能找到一款帮我做计划并落地执行的工具，先后尝试过很多不同类型的工具，比如各种 Todo 任务工具、项目管理工具以及笔记文档工具等，始终没有一款工具能够帮我做长远计划并且又能落地执行（比如，当计划不如预期后很难调整，以及无法将计划落实到每天的安排），遂决定自己开发一款 app 来满足该需求。

### 尝试过的工具

以下是一些我尝试过的工具，最接近的是 Notion 的 Timeline 视图，可惜更新和维护计划还是非常麻烦，希望以后能通过更新改善。

#### Todo 任务工具

- 滴答清单
- Sorted
- Things
- Microsoft To Do
- Agenda
- Todoist
- Any.do
- Asana
- OmniFocus

#### 项目管理工具

- Trello
- Google Sheet
- Excel
- Gantt 图

#### 笔记文档工具

- Notion
- Evernote

### App 原型设计

这是最初探索和验证产品 idea 的 app 原型设计的[Figma 链接](https://www.figma.com/proto/Fu798a22H3V7v9FX5Uwq8y/Timeline-app?node-id=107%3A1355&scaling=scale-down&page-id=28%3A178&starting-point-node-id=107%3A1355)。

### 市场调研

为了了解产品的潜在用户和市场，今年 5 月份我制作了 app 的第一版原型，以此采访过几位身边的同事和朋友，对产品的价值主张进行了初步验证（确定了目标用户和使用场景），同时我还在一些论坛群组里发过一支 GoPlan app 宣传短片（[抖音视频链接](https://v.douyin.com/FPp9Kvc/)），测试一下市场反响，当时有大约 30 人主动咨询产品如何使用。过程中也没有发现能完美取代 GoPlan 的产品。

### 为什么要开发 GoPlan

当然前面的原型设计和市场调研都只是初步的试探，无法验证产品一定是有真实需求的。但由于我自己对这个产品的需求由来已久，我最后决定，即使实际上只有我一个人觉得产品有用，也就足够了。于是有了今天 GoPlan 的上线。

目前的产品功能还是非常 MVP 的状态，属于基本能用。后面是否还会继续开发就完全取决于市场反应了。大家如果觉得 GoPlan 对你有用，不妨通过在线客服或 Github issue 联系作者，鼓励持续开发。
