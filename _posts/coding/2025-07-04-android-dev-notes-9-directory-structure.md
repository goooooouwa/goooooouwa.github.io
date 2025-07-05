---
title: Android编程笔记（九）：推荐的代码库目录结构
category: coding
tags: android directory-structure
published: true
---
## 概览

![android-directory-structure.png]({{site.baseurl}}/assets/images/android-directory-structure.png)

我个人习惯使用以下目录：

- api
- db
- utilities
- ui
- viewmodels
- workers

### DB子目录

This directory houses all DB-related components:
- Database: The main access point to your app's persistent data. 
- Data Entities: Classes that represent tables in your database.
- Data Access Objects (Dao): Interfaces or abstract classes that define methods for accessing and manipulating data in your database. 

src/main/java/com/example/myapplication/db:

- Database.kt
- ADao.kt
- A.kt
- BDao.kt
- B.kt

### UI组件子目录

This directory houses all UI-related components:
- Activities: The entry points for user interaction. 
- Fragments: Reusable UI components that can be combined within Activities. 
- Custom Views: Specialized UI elements created by extending existing View classes. 
- Adapters: Classes that bridge data and UI elements for displaying lists or grids.

src/main/java/com/example/myapplication/ui:

- MainActivity.kt
- AListFragment.kt
- ADetailsFragment.kt
- ARecyclerViewAdapter.kt
- BListFragment.kt
- BDetailsFragment.kt
- CFragment.kt

### View Models子目录

viewmodels directory:
- Contains ViewModel classes that manages UI-related data and survives configuration changes (like screen rotation).

src/main/java/com/example/myapplication/viewmodel:

- AViewModel.kt
- BViewModel.kt

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


## References:

- https://stackoverflow.com/a/63650013
- https://blog.stackademic.com/organizing-your-android-app-with-mvvm-a-package-hierarchy-guide-c1c0f48fba60

