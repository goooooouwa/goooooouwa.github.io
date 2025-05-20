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

### How to update list data

1. Provide method to update dataset

```kotlin
class StudentRecyclerViewAdapter(): RecyclerView.Adapter<StudentRecyclerViewAdapter.ViewHolder>() {

    var studentList: List<Student> = emptyList();

    fun setStudentsList(students: List<Student>) {
        studentList = students
    }

    // ...
}
```

2. Call the method to update dataset

```kotlin
studentRecyclerViewAdapter.setStudentsList(students)
```

3. notify the Adapter about the event

```kotlin
studentRecyclerViewAdapter.notifyItemRangeInserted(0, students.size)
```

### References:

- https://developer.android.com/develop/ui/views/layout/recyclerview
