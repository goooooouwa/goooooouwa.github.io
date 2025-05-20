---
title: Android应用Activity编程笔记
category: coding
tags: android activity
published: true
---

## 理解`Activity`

`Activity`简单理解即是MVC中的C，即View Controller。以下是一段常见的`Activity`类的代码：

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
		
		// ...
    }
}
```

## 理解`setContentView()`方法

函数定义：

```kotlin
public void setContentView (View view)
```

功能：

`setContentView()`用来为Activity设置其顶层视图，该视图可以包含其他子视图。

Set the activity content to an explicit view. This view is placed directly into the activity's view hierarchy. It can itself be a complex view hierarchy. When calling this method, the **layout parameters of the specified view are ignored**. Both **the width and the height of the view are set by default to ViewGroup.LayoutParams.MATCH_PARENT**. To use your own layout parameters, invoke `setContentView(android.view.View, android.view.ViewGroup.LayoutParams)` instead.

## 理解`LayoutInflater`的用途以及如何用它创建视图

在Android中经常见到以下代码用于动态添加视图到现有视图中：

```kotlin
// Create a new view, which defines the UI of the list item
val view = LayoutInflater.from(viewGroup.context)
            .inflate(R.layout.text_row_item, viewGroup, false)
containerView.addView(view);
```

### `LayoutInflater`的用途

Instantiates a layout XML file into its corresponding View objects. It is never used directly. Instead, use `Activity.getLayoutInflater()` or `Context.getSystemService` to retrieve a standard `LayoutInflater` instance that is already hooked up to the current context and correctly configured for the device you are running on.

For performance reasons, view inflation relies heavily on pre-processing of XML files that is done at build time. Therefore, it is not currently possible to use `LayoutInflater` with an `XmlPullParser` over a plain XML file at runtime; it only works with an `XmlPullParser` returned from a compiled resource (R.something file.)

### How to inflat a view

1. Get the `LayoutInflater`:  
  Obtain a `LayoutInflater` instance from your context. This can be done using `Activity.getLayoutInflater()` or `getSystemService(Context.LAYOUT_INFLATER_SERVICE)`.
2. Inflate the Layout:  
  Call the `inflate()` method of the `LayoutInflater` instance, providing the resource ID of the XML layout file and a `ViewGroup` (which will be the parent of the inflated view).
3. Add the Inflated View:  
  If you're not inflating directly into a parent view (e.g., using attachToRoot = true), you'll need to manually add the inflated View to its parent `ViewGroup` using `addView()`.

接下来，让我们逐步理解前面代码用到的两个方法以及`Context`对象。

#### 理解`from()`方法

函数定义：

```kotlin
public static LayoutInflater from (Context context)
```

功能：Obtains the LayoutInflater from the given context.

#### 理解`inflate()`方法

函数定义：

```kotlin
public View inflate (int resource, 
                ViewGroup root)
```

```kotlin
public View inflate (int resource, 
                ViewGroup root, 
                boolean attachToRoot)
```

功能：Inflate a new view hierarchy from the specified xml resource. Throws InflateException if there is an error.

#### 理解`Context`对象

Interface to global information about an application environment. This is an abstract class whose implementation is provided by the Android system. It allows access to application-specific resources and classes, as well as up-calls for application-level operations such as launching activities, broadcasting and receiving intents, etc.

在Android开发里Context参数很常见。使用Context参数，单例可完成启动activity、获取项目资源，查找应用的私有存储空间等任务。

注意，在get(Context)方法里，我们并没有直接将Context参数传给构造方法。该Context可能是一个Activity，也可能是另一个Context对象，如Service。在应用的整个生命周期里，我们无法保证需要用到Context时，Context就一定会存在。因此，为保证单例总是有Context可以使用，可调用getApplicationContext()方法，将不确定是否存在的Context替换成application context。application context是针对应用的全局性Context。任何时候，只要是应用层面的单例，就应该一直使用application context。

## References:

- https://developer.android.com/reference/android/view/LayoutInflater
- https://book.douban.com/subject/25848404/
- https://developer.android.com/reference/android/app/Activity#setContentView(android.view.View)
- https://developer.android.com/guide/components/activities/intro-activities
