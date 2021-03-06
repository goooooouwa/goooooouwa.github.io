---
category: productivity
date: 2019-03-28
title: 想法管理方案
---

结论：用Notes（or Drafts）记录零碎的想法，没用的就删掉，需要保存的就存到Evernote，需要进一步编辑的就在iA writer继续编辑。

## 需求

* 快速记录
* 可靠存储，不会误改（想法就是要易于修改吧？最好有版本）
* 快速查找（分类，tagging）
* 易于更新, grow（编辑，合并）
* 轻松分享（谁会想看你随意的想法？instead，分享grow 整理后的文章）

## 苦恼

* 有许多想法长期停留在想法阶段（也许永远如此），一大堆零碎的想法在工作区造成思想负担。
* 想让人知道我有很多想法（这个出发点不切实际，没人想看你的一堆随意想法）

## 困惑

**想法需要以文件形式存储吗？**

其实以什么形式存储不重要，只要能方便的创建、查找、编辑、删除（CRUD）就行了。如果有编辑器可以方便的做到以上几点即可。

Options:

- Drafts：可以
- iA writer：管理文件不方便（比如删除没有快捷键）
- VS Code：不支持手机

Choice: Drafts

**final的想法长期在工作区有思想负担，如何处理？**

Options:

- hide起来（目录、tag）
- 存起来
	- 存到哪里？
	- 存成文件太重了？（主要是要有方便的管理方式）

Choice: 用目录管理不同内容，维护一个干净的工作区（Inbox），就不会有心理负担。

- untagged as inbox
- if active thought, put it in thoughts folder.
- if final thought, store in Evernote and publish in postach.io.

**Journal如何写比较方便？**

Options:

- Evernote
- Drafts
- iA writer
- VS Code
- Card Diary （export as Markdown)

Choice: write in iA writer. iA writer写作很舒服，适合Journal。 Drafts记录的想法也可以发送到iA writer（保存为Journal文件）。

**想法本身需要分享吗？**

有的可以分享，有的不需要。Drafts可以很方便的分享。

## 想法生命周期: 

出现，记录，合并、更新，公开、分享、发布

文件对于想法管理大重了（只想管理内容和标签，要能方便的搜索查找）。 

想法有时需要永久保存(journal)，有时需要grow（copy on write)。 

## 候选

* Notes
* Drafts
* Evernote
* GitHub repo
* Zoho notebook （形式主义，开发能力不够强）

## Proposal: 

想法用drafts快速记录并发送到Evernote等待后续更新 
如果希望持久化当前版本，就发布到合适的平台（Twitter、微博、朋友圈、博客），发布不影响想法的后续更新。 
Evernote作为所有想法的单一数据源（single source of truth）。 
想法内容逐渐成型就用Markdown编辑器排版，发布成博客（可以从Evernote中删除）。

### 方案的downside

Evernote Note style can easily get messy.

### 依赖的功能

Evernote (simple html, e.g. rich text, no images, no tables, no attachments) 
-> markdown -> Jekyll

### 工具对比

#### ever2simple: 

*  Markdown text support 
*  不支持图片 
*  不支持code block

#### pistachio.io

pistachio.io as public thoughts.

#### geeknotes:

Pros:

* Support markdown to note
* Support note to markdown
* Support image tag
* Support direct md file to Evernote
* Support CLI editor, e.g. vim

Cons:

* Note format is a bit messy (need simplify format)
* Not so good with Jekyll front matter
* Not support GUI editor, e.g. VS code

#### everMonkey:

Pros:

* Support markdown to note
* Support direct md file to Evernote
* Support image tag
* Support Chinese（中文）
* Support GUI editor, e.g. VS code

Cons:

* Note format is a bit messy (need simplify format)
* Not so good with Jekyll front matter
* Not support note to markdown (only displayed as is)
