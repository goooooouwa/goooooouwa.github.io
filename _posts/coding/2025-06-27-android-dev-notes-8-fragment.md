## Fragment

### Difference and uses of `onCreate()`, `onCreateView()` in fragments

**[`onCreate()`](http://developer.android.com/reference/android/app/Fragment.html#onCreate%28android.os.Bundle%29):**

The `onCreate()` method in a `Fragment` is **called after the `Activity`'s `onAttachFragment()`** but before that `Fragment`'s `onCreateView()`.  
In this method, you can assign variables, get `Intent` extras, and **anything else that doesn't involve the View hierarchy** (i.e. non-graphical initialisations). This is because this method can be called when the `Activity`'s `onCreate()` is not finished, and so trying to access the View hierarchy here may result in a crash.

**[`onCreateView()`](http://developer.android.com/reference/android/app/Fragment.html#onCreateView%28android.view.LayoutInflater%2C+android.view.ViewGroup%2C+android.os.Bundle%29):**

After the `onCreate()` is called (in the `Fragment`), the `Fragment`'s `onCreateView()` is called. You can assign your `View` variables and **do any graphical initialisations**. You are expected to return a `View` from this method, and this is the main UI view, but if your `Fragment` does not use any layouts or graphics, you can return `null` (happens by default if you don't override).

**To sum up**

They are all called in the `Fragment` but are called at different times.  
The `onCreate()` is called first, for doing any non-graphical initialisations. Next, you can assign and declare any `View` variables you want to use in `onCreateView()`.

## References:

- https://stackoverflow.com/questions/28929637/difference-and-uses-of-oncreate-oncreateview-and-onactivitycreated-in-fra
