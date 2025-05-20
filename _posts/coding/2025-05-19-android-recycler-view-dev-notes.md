---
title: Android应用RecyclerView编程笔记
category: coding
tags: android recycler-view
published: true
---

## 实现RecyclerView adapter和view holder以及item view layout file

Once you determine your layout, you need to implement your `Adapter` and `ViewHolder`. These two classes work together to define how your data is displayed. The ViewHolder is a wrapper around a View that contains the layout for an individual item in the list. The Adapter creates ViewHolder objects as needed and also sets the data for those views. The process of associating views to their data is called binding.

### Example RecylerView adapter & view holder code

```kotlin
class CustomAdapter(private val dataSet: Array<String>) :
        RecyclerView.Adapter<CustomAdapter.ViewHolder>() {

    /**
     * Provide a reference to the type of views that you are using
     * (custom ViewHolder)
     */
    class ViewHolder(view: View) : RecyclerView.ViewHolder(view) {
        val textView: TextView

        init {
            // Define click listener for the ViewHolder's View
            textView = view.findViewById(R.id.textView)
        }
    }

    // Create new views (invoked by the layout manager)
    override fun onCreateViewHolder(viewGroup: ViewGroup, viewType: Int): ViewHolder {
        // Create a new view, which defines the UI of the list item
        val view = LayoutInflater.from(viewGroup.context)
                .inflate(R.layout.text_row_item, viewGroup, false)

        return ViewHolder(view)
    }

    // Replace the contents of a view (invoked by the layout manager)
    override fun onBindViewHolder(viewHolder: ViewHolder, position: Int) {

        // Get element from your dataset at this position and replace the
        // contents of the view with that element
        viewHolder.textView.text = dataSet[position]
    }

    // Return the size of your dataset (invoked by the layout manager)
    override fun getItemCount() = dataSet.size

}
```

### Example item view layout file

The layout for the each view item is defined in an XML layout file. Below is an example item view XML layout file:

```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="@dimen/list_item_height"
    android:layout_marginLeft="@dimen/margin_medium"
    android:layout_marginRight="@dimen/margin_medium"
    android:gravity="center_vertical">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/element_text"/>
</FrameLayout>
```

### How to use RecyclerView

The following code snippet shows how you can use the RecyclerView.

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val dataset = arrayOf("January", "February", "March")
        val customAdapter = CustomAdapter(dataset)

        val recyclerView: RecyclerView = findViewById(R.id.recycler_view)
        recyclerView.layoutManager = LinearLayoutManager(this)
        recyclerView.adapter = customAdapter

    }

}
```

## Understand `LayoutInflater` & how to inflate a view

### `LayoutInflater`的用途

Instantiates a layout XML file into its corresponding View objects. It is never used directly. Instead, use `Activity.getLayoutInflater()` or `Context.getSystemService` to retrieve a standard `LayoutInflater` instance that is already hooked up to the current context and correctly configured for the device you are running on.

For performance reasons, view inflation relies heavily on pre-processing of XML files that is done at build time. Therefore, it is not currently possible to use `LayoutInflater` with an `XmlPullParser` over a plain XML file at runtime; it only works with an `XmlPullParser` returned from a compiled resource (R.something file.)

### How to inflat a view

在Android中经常见到以下代码来创建视图：

```kotlin
// Create a new view, which defines the UI of the list item
val view = LayoutInflater.from(viewGroup.context)
            .inflate(R.layout.text_row_item, viewGroup, false)
containerView.addView(view);
```

接下来，让我们拆分别理解这里用到的两个方法以及`Context`对象。

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

## 理解`setContentView()`方法

`setContentView()`用来为Activity设置其顶层视图，该视图可以包含其他子视图。例如以下Activity代码：

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
		
		// ...
    }
}
```

函数定义：

```kotlin
public void setContentView (View view)
```

功能：Set the activity content to an explicit view. This view is placed directly into the activity's view hierarchy. It can itself be a complex view hierarchy. When calling this method, the **layout parameters of the specified view are ignored**. Both **the width and the height of the view are set by default to ViewGroup.LayoutParams.MATCH_PARENT**. To use your own layout parameters, invoke `setContentView(android.view.View, android.view.ViewGroup.LayoutParams)` instead.

## References:

- https://developer.android.com/develop/ui/views/layout/recyclerview
- https://developer.android.com/reference/android/view/LayoutInflater
- android权威指南
- https://developer.android.com/reference/android/app/Activity#setContentView(android.view.View)
- https://developer.android.com/guide/components/activities/intro-activities