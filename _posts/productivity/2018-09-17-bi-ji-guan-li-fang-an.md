---
category: productivity
date: 2018-09-17
title: 笔记管理方案
---

2018-09-17-things-evernote-not-good-at

Evernote 不适合做的事

Evernote 可以做很多事，比如：

- 项目管理
- 文本编辑器
- 提醒事项
- 文件存储
- 文章收集
- 书签管理

但在我使用 Evernote 很久后，我逐渐发现有比 Evernote 更适合的工具：

- 项目管理：在线协作平台，如 Google Docs
- 文本编辑器：Markdown 编辑器，如 Typora
- 提醒事项：单独的 Todo app，如 iOS Reminders
- 文件存储：网络硬盘，如 iCloud Drive
- 文章收集：Read it Later 服务，如 Instapaper
- 书签管理：浏览器书签或书签服务，如 Chrome Bookmarks

## 结论

Evernote 最擅长做的是笔记的存储，专业的事还是该交给专业的工具去做。可以将其他工具与 Evernote 结合使用（通过类似 IFTTT 的服务）。

2018-09-17-how-to-organize-notes

如何整理笔记：理论与实践

## 笔记管理的理想状态

### 笔记内容

- 格式统一
- 标题表意
- 内容纯粹（省去无关内容）

### 笔记组织

理想的笔记组织具有以下三个属性。

#### 还原

能将笔记还原到诞生的上下文中，比如书籍和文章，便于还原回忆。如果上下文与内容无关则不必，比如网页片段，能链接回原页面。

#### 提炼

便于将笔记形成大纲 outline 或 mindmap，以表明内容关系，提炼 overview。

#### 温习

便于将笔记做成 Flashcards，便于巩固记忆。

![how-to-organize-notes]({{site.baseurl}}/assets/images/yo3TQnE.png)

## 实践方法

如何针对所有类型（书籍，文章，内容片段）的学习笔记做到以上几点？

### 笔记管理 workflow

#### Step 1：记笔记

直接在知识上下文中记笔记，上下文包括：

- 电子书：iBooks、Kindle
- PDF 文档：Preview
- 文章：Instapaper
- 网页片段：Evernote Web Clipper
- 图片：Skitch

#### Step 2：存储笔记

将各处笔记导入 Evernote 统一存储，方法如下：

- ePub：iBooks app 分享笔记，按书籍为单位存储笔记
- mobi：Kindle app 分享笔记，按书籍为单位存储笔记
- PDF：[skim](https://skim-app.sourceforge.io/)提取笔记，按文档为单位存储笔记
- Instapaper：[Instapaper highlights exporter](https://chrome.google.com/webstore/detail/instapaper-highlights-exp/oiklmlodhebcmaijgmheoafagfhbeohm)，按文章为单位存储笔记
- 网页片段：直接保存，按网页为单位存储笔记
- 图片：直接保存

#### Step 3：提炼 Overview

将笔记导出，整理成 outline 或 mindmap，方法如下：

- outline：
  1. 将相关笔记生成 Table of Contents
  2. 将标题整理成 outline，以 Markdown 格式保存
- mindmap：
  1. 将 Markdown 格式 outline 导入生成 mindmap

#### Step 4：温习

将笔记导出，使用 Flashcards（比如 Reflect app）温习笔记

<iframe src="http://www.xmind.net/embed/Ng8c" width="900px" height="540px" frameborder="0" scrolling="no"></iframe>

---

Note: 以上理想笔记管理思路来自于[MarginNote](https://marginnote.com/)的 all in one place 笔记法。

![margin-note-all-in-one-place]({{site.baseurl}}/assets/images/RJOY6rJ.png)

2018-09-14-Migrate away from Evernote

## Evernote organization 2018/9/14

File types extracted out of Evernote:

- Articles -> Instapaper
- Bookmarks -> Browser (backup as HTML files)
- Blog posts -> markdown files
- Favorite Articles -> Pages documents (exportable to ePub & azw3 & PDF files)
- documents -> iCloud Drive

Evernote focusing on taking notes( text, handwriting script)

Convert:
Handwritten script to text(OCR): Google Translate
Voice to text: Keyboard Dictation

Text to voice: iOS accessibilty

## note types

待整理笔记的类型分析：

| 类型     | 格式                         | 例子                           | 用途                 | 性质                                                  | 改进建议                                           |
| -------- | ---------------------------- | ------------------------------ | -------------------- | ----------------------------------------------------- | -------------------------------------------------- |
| 简单文本 | 文本、标记图片、手写笔记扫描 | 学习笔记、头脑风暴、写作、思考 | 可编辑内容           | 原创                                                  | 当内容积累足以形成文章后，用 Typora 整合编辑、排版 |
| 富文本   | 网页剪切                     | 问答、知识                     | 提取内容、保存 as is | 转载                                                  | 保存网页时，尽量简化格式，仅保留必要内容           |
| 文件     | 图片、PDF、音频、Zip 包      | 身份证、体检报告、网页快照     | 记录、保存 as is     | 原创、转载｜存储到文件系统，Evernote 只保存可编辑内容 |
| 书签     | 链接                         | 新闻、文章                     | 记录                 | 引用                                                  | 用浏览器保存书签                                   |

Q：是否将网页剪切和笔记区分开？或者说，笔记中含有网页剪切或资源图片，是否属于侵权？

应该 OK 吧，关键是比例。根本的问题是：笔记是否具有原创属性？应该算吧。因此决定将网页剪切（全文内容除外）视作为我的笔记的一部分，即简单文本和网页剪切全都是我的原创内容。

Q：笔记是否可供他人学习？

可以，只要整理的条理清晰，有二次加工（否则别人直接看链接就好了吧）。直接 publish 笔记来 share 吧，没有想到更好的 share 方案。

记笔记的主要需求及解决方案：

- 将原创与转载区分开：将文章区分开，将网页剪切（全文内容除外）视作为我的笔记的一部分。
- 将信息聚合形成可 consume 的产出：文章、学习笔记、文件，逐步积累提炼。
- 低成本的维护方式：提取内容，不标记则无需截图
- 快速定位：tags
- 可视化：画脑图、建 table of contents

场景

- 学习：遇到一个问题，上网搜索，找到有用的网页，获取只读模式的文章，get ride off clusters, 标记、注解
- 学习：遇到一个问题，上网搜索，找到有用的 PDF 文件，下载文件，标记、注解
- 学习：遇到一个问题，上网搜索，找到有用的电子书（ePub，mobi），下载，在电子书阅读器中阅读，记笔记
- 创作：有任何想法，随手记下来（文本、手写、白板、文档）
- 记录：存储重要信息（拍照、文本、剪切网页、图片、文件）

Q：笔记是应该 strip off 原始文件，还是 stay with 原始文件？

最好是能 stay together，并且可以方便的查阅。但是有一些考虑，比如能否导出。对于 ePub, mobi, pdf，笔记如果跟文件一起，因为文件比较适合放在文件系统，则笔记会跟文件走，所以会比较分散，无法 search all in one place，可以考虑定期导出笔记。

### ePub, kindle 电子书

ePub, kindle 电子书的笔记可以和书一起 Sync，也可以导出。

### PDF

PDF 可以用 Preview 笔记，笔记可以用 skim 导出。

### 网页

对于网页资源这种无法 stay together 的文件，笔记带上原始文件的引用 url 也算是 stay together 吧，也可以随时找到原始内容，只要网页还生效。也可以考虑购买 Diggo。

### 屏幕截图

屏幕截图的原始文件可能是任何东西，甚至根本不是文件，所以如果是以上列举类型，尽量不要截图 strip off 吧。无法找到原始文件就截图，是 last resorts。

## 对笔记的分析

尝试将相关笔记提取成 mindmap 后，我发现笔记的本质属性：笔记是提取出来的信息片段，是零散的、不完整的、不成体系的。

一条笔记应该是关于一篇文章、一本书、一段内容的所有 highlights 和 notes 的集合，信息聚合。如果需要打散可以另行处理。

Q: 是否可能将本质上零散、不成体系的信息片段构成完整的知识体系，进而带来价值产出呢？

我自己首先要有一个知识体系，再将笔记和其他资源（文章、文件）挂载上去，才能保证知识的系统化。心里要有个谱，所以得先建立知识体系。

Q: 将笔记间 high level 关系提炼成 outline 和 mindmap 是否有价值？

分类、标签、搜索可以很方便的找到单个笔记，但如果没有对笔记间关系的 overview，笔记本就是一堆零散的碎片。Outline 和 mindmap 的价值就是形成笔记间的关联，这有助于知识体系的搭建。

Q: Outline，Mindmap 可以用来提取笔记间的这种关系信息。挑战在于，如何在动态的笔记管理中维护这些关系信息?

维护一份 Markdown 格式的 outline，作为 single source of truth。每当修改或添加笔记标题后，生成 Table of Contents，并以此更新 Outline（markdown)，将更新导入 mindmap。

## Kinds of writing:

Pieces information to hold privately for a while
Pieces information to hold privately permanently
Thoughts to brew for a while
Interesting thoughts to share
Original Publication (maybe turning from thoughts)
Knowledge organization ( citations, digests, screenshots)
