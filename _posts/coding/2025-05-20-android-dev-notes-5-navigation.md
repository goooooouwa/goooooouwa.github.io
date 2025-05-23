---
title: Android编程笔记（五）：Navigation
category: coding
tags: android navigation
published: true
---

* TOC
{:toc}

## 关键概念

The following table provides an overview of the key concepts in navigation and the main types that you use to implement them.

| Concept     | Purpose        | Type    |
|-------------|----------------|---------|
| Controller  |  `NavController`是控制页面导航的核心组件，它掌管着navigation graph，提供了在页面间导航的各种方法。It holds the navigation graph and exposes methods that allow your app to move between the destinations in the graph. The central coordinator for managing navigation between destinations. The controller offers methods for navigating between destinations, handling deep links, managing the back stack, and more. | `NavController` |
| Graph       | `NavGraph`是一种用于定义应用中所有导航目的地以及目的地之间关系的数据结构。A data structure that defines all the navigation destinations within the app and how they connect together. | `NavGraph` |
| Host        | Host就是一个展示当前导航页面的视图容器，比如一个Fragment。A UI element that contains the current navigation destination. That is, when a user navigates through an app, the app essentially swaps destinations in and out of the navigation host.  | Compose: `NavHost`, Fragments: `NavHostFragment` |
| Destination | Desitination这是一个概念，代表这navigation graph中的一个结点。A node in the navigation graph. When the user navigates to this node, the host displays its content. | `NavDestination` Typically created when constructing the navigation graph. |
| Route       | 路由用于导航到特定页面。Uniquely identifies a destination and any data required by it.You can navigate using routes. Routes take you to destinations. | Any serializable data type. |

### Host、navigation controller和graph之间的关系

Each `NavHost` you create has its own corresponding `NavController`. The `NavController` provides access to the `NavHost`'s graph.

## 如何设置导航

0. 安装navigation依赖
1. 创建navigation graph
2. 创建navigation host
3. 获取navigation controller
4. 进行页面导航


### 0. 安装navigation依赖

To include navigation support in your project, add the following dependencies to your app's `build.gradle` file:

```kotlin
plugins {
  // Kotlin serialization plugin for type safe routes and navigation arguments
  kotlin("plugin.serialization") version "2.0.21"
}

dependencies {
  val nav_version = "2.9.0"

  // Views/Fragments integration
  implementation("androidx.navigation:navigation-fragment:$nav_version")
  implementation("androidx.navigation:navigation-ui:$nav_version")

  // optional - Jetpack Compose integration
  implementation("androidx.navigation:navigation-compose:$nav_version")

  // // optional - Feature module support for Fragments
  implementation("androidx.navigation:navigation-dynamic-features-fragment:$nav_version")

  // Testing Navigation
  androidTestImplementation("androidx.navigation:navigation-testing:$nav_version")

  // JSON serialization library, works with the Kotlin serialization plugin
  implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
}
```

For information on adding other architecture components to your project, see Add components to your project.



### 1. 创建navigation graph

When using fragments with the views UI framework, use a NavHostFragment as the host. There are several ways to create a navigation graph:
- Programmatically: Use the Kotlin DSL to create a NavGraph and directly apply it on the NavHostFragment.
  - The createGraph() function used with the Kotlin DSL for both fragments and Compose is the same.
- XML: Write your navigation host and graph directly in XML.
- Android Studio editor: Use the GUI editor in Android Studio to create and adjust your graph as an XML resource file.

In Android Studio:
1. right click on the `res` folder
2. Select New -> Android Resource File
3. Set `Resource Type`  as **Navigation**
4. Set `File name` for the graph, e.g. `nav_graph`

### 1.1 使用Navigation Editor设计graph及其destinations和actions

#### Add destinations

To add a new destination using the Navigation Editor, do the following:

1. In the Navigation Editor, click the **New Destination** icon,
2. Select an existing destination in the drop-down or Click **Create new destination** button to create a new destination,
3. (If creating a new destination) In the **New Android Component** dialog that appears, create your fragment.

#### Add actions

You can use the Navigation Editor to connect two destinations by doing the following:

1. In the **Design** tab, hold the pointer over the right side of the destination that you want users to navigate from. A circle appears over the right side of the destination.
2. Drag your cursor over the destination you want users to navigate to, and release. The resulting line between the two destinations represents an action.

### 2. 创建navigation host

You can also use the Layout Editor to add a `NavHostFragment` to an activity by doing the following:

1. In your list of project files, double-click your activity's layout XML file to open it in the Layout Editor.
2. Within the Palette pane, choose the Containers category; alternatively, search for "NavHostFragment".
3. Drag the `NavHostFragment` view onto your activity.
4. In the **Navigation Graphs** dialog that appears, choose the corresponding navigation graph to associate with this `NavHostFragment`, and then click OK.

## 3. 获取navigation controller

You can retrieve your `NavController` using one of the following methods depending on the context:

1. `Fragment.findNavController()`
2. `View.findNavController()`
3. `Activity.findNavController(viewId: Int)`

Typically, you first get a `NavHostFragment`, and then retrieve the `NavController` from the fragment. The following snippet demonstrates this:

```kotlin
// retrieve the `NavController` from the fragment
val navHostFragment =
    supportFragmentManager.findFragmentById(R.id.nav_host_fragment) as NavHostFragment
val navController = navHostFragment.navController

// alternatively, retrieve the `NavController` within an Activity
val navController = findNavController(R.id.nav_host_fragment_activity_main)
```

## 4. Navigate to a destination 

### Use a NavController
The key type you use to move between destinations is the `NavController`.

### Navigate
Regardless of which UI framework you use, there is a single function you can use to navigate to a destination: `NavController.navigate()`.

There are many overloads available for `navigate()`. The overload you should choose corresponds to your exact context. For example, you should use one overload when navigating to a composable and another when navigating to a view.

#### Navigate to a destination using integer ID

To navigate to a destination using an integer ID, call the `navigate(int)` overload. It takes the resource ID of either an action or a destination. The following code snippet shows how you can use this overload to navigate to the `ViewTransactionsFragment`:

```kotlin
viewTransactionsButton.setOnClickListener { view ->
  view.findNavController().navigate(R.id.viewTransactionsAction)
}
```

**When navigating using IDs, you should use actions where possible**. Actions provide additional information in your navigation graph, visually showing how your destinations connect to each other.

## 理解navigation graph

Navigation graph包含destinations和actions. 以下为一个navigation graph的XML代码示例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    app:startDestination="@id/blankFragment">
    <fragment
        android:id="@+id/blankFragment"
        android:name="com.example.cashdog.cashdog.BlankFragment"
        android:label="@string/label_blank"
        tools:layout="@layout/fragment_blank" />
</navigation>
```

###  理解destination

Understand the attributes for a destination:

- The **Type**` field indicates whether the destination is implemented as a fragment, activity, or other custom class in your source code.
- The **Label**` field contains the user-readable name of the destination. This might be surfaced to the UI—for example, if you connect the `NavGraph` to a `Toolbar` using `setupWithNavController()`. For this reason, use resource strings for this value.
- The **ID**` field contains the destination ID, which is used to refer to the destination in code.
- The **Class**` drop-down shows the name of the class that is associated with the destination. Click this drop-down to change the associated class to another destination type.

#### 理解3种destination type

There are three general types of destinations: hosted, dialog, and activity. The following table outlines these three destination types and their purposes.

| Type | Description | Use cases |
| --- | --- | --- |
| Hosted | Hosted类型的导航目的地会填充整个nav host视图区域，适用于页面间的导航。Fills the entire navigation host. That is, the size of a hosted destination is the same as the size of the navigation host and previous destinations are not visible. | Main and detail screens. |
| Dialog | Dialog类型的导航目的地会以遮罩的形式出现在nav host视图区域，前一个导航页面在遮罩的下方依然可见，适用于各种弹窗、对话框等。Presents overlay UI components. This UI is not tied to the location of the navigation host or its size. Previous destinations are visible underneath the destination. | Alerts, selections, forms. |
| Activity | Activity类目的地即应用中的其他Activity，用于从navigation graph跳转到其他Activity。Represents unique screens or features within the app. | Serve as an exit point to the navigation graph that starts a new Android activity that is managed separately from the Navigation component.<br><br>**In modern Android development, an app consists of a single activity**. Activity destinations are therefore best used when interacting with third party activities or as part of [the migration process](https://developer.android.com/guide/navigation/migrate). |

#### 理解placeholder destinations
You can use placeholders to represent unimplemented destinations. A placeholder serves as a visual representation of a destination. Within the Navigation Editor, you can use placeholders just as you would any other destination.

Note: You must change the Class attribute of your placeholders to existing destinations before running your app. Placeholders don't cause compilation errors, and if you attempt to navigate to a placeholder destination, the app throws a runtime exception.

### 理解action

With actions, you're representing the different paths that users can take through your app. Note that to actually navigate to destinations, you still need to write the code to perform the navigation.

In your navigation graph, actions are represented by <action> elements. At a minimum, an action contains its own ID and the ID of the destination to which a user should be taken.

Click the arrow to highlight the action. The following attributes appear in the **Attributes** panel:

- The **Type** field contains "Action".
- The **ID** field contains the ID for the action.
- The **Destination** field contains the ID for the destination fragment or activity.

## References:

- https://developer.android.com/guide/navigation
- https://developer.android.com/guide/navigation/navcontroller
- https://developer.android.com/guide/navigation/design
- https://developer.android.com/guide/navigation/use-graph/navigate
- https://developer.android.com/guide/navigation/design/editor
