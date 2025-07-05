---
title: Android编程笔记（九）：典型代码库目录结构
category: coding
tags: android directory-structure
published: true
---
### 源代码根目录

src/main/java/com/example/myapplication:

- MainActivity.kt
- AListFragment.kt
- ADetailsFragment.kt
- ARecyclerViewAdapter.kt
- BListFragment.kt
- BDetailsFragment.kt
- CFragment.kt

### View model子目录

src/main/java/com/example/myapplication/view-models:

- AViewModel.kt
- BViewModel.kt

### DB子目录
src/main/java/com/example/myapplication/db:

- Database.kt
- ADao.kt
- A.kt
- BDao.kt
- B.kt

### UI布局子目录
src/main/res/layout:

- activity_main.xml
- fragment_a_list.xml
- fragment_a_details.xml
- fragment_b_list.xml
- fragment_b_details.xml
- fragment_c.xml
- list_item.xml

### UI导航子目录
src/main/res/navigation:

- nav_graph.xml

### AndroidManifest声明文件

src/main:

- AndroidManifest.xml