* TOC
{:toc}

## How to use fragments

A [fragment](https://developer.android.com/guide/fragments) represents a modular portion of the user interface within an activity. A fragment has its own lifecycle, receives its own input events, and you can add or remove fragments while the containing activity is running.

This document describes how to create a fragment and include it in an activity.

### Setup your environment

Fragments require a dependency on the [AndroidX Fragment library](https://developer.android.com/jetpack/androidx/releases/fragment). You need to add the [Google Maven repository](https://developer.android.com/studio/build/dependencies#google-maven) to your project's `settings.gradle` file in order to include this dependency.

```kotlin
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        ...
    }
}
```

To include the AndroidX Fragment library to your project, add the following dependencies in your app's `build.gradle` file:

```kotlin
dependencies {
    val fragment_version = "1.8.8"

    // Java language implementation
    implementation("androidx.fragment:fragment:$fragment_version")
    // Kotlin
    implementation("androidx.fragment:fragment-ktx:$fragment_version")
}
```

### Create a fragment class

To create a fragment, extend the AndroidX [`Fragment`](https://developer.android.com/reference/androidx/fragment/app/Fragment) class, and override its methods to insert your app logic, similar to the way you would create an [`Activity`](https://developer.android.com/reference/android/app/Activity) class. To create a minimal fragment that defines its own layout, provide your fragment's layout resource to the base constructor, as shown in the following example:


```kotlin
class ExampleFragment : Fragment(R.layout.example_fragment)
```

### Add a fragment to an activity

Generally, your fragment must be embedded within an AndroidX [`FragmentActivity`](https://developer.android.com/reference/androidx/fragment/app/FragmentActivity) to contribute a portion of UI to that activity's layout. `FragmentActivity` is the base class for [`AppCompatActivity`](https://developer.android.com/reference/androidx/appcompat/app/AppCompatActivity), so if you're already subclassing `AppCompatActivity` to provide backward compatibility in your app, then you do not need to change your activity base class.

You can add your fragment to the activity's view hierarchy either by defining the fragment in your activity's layout file or by defining a fragment container in your activity's layout file and then programmatically adding the fragment from within your activity. In either case, you need to add a [`FragmentContainerView`](https://developer.android.com/reference/androidx/fragment/app/FragmentContainerView) that defines the location where the fragment should be placed within the activity's view hierarchy. It is strongly recommended to always use a `FragmentContainerView` as the container for fragments, as `FragmentContainerView` includes fixes specific to fragments that other view groups such as `FrameLayout` do not provide.

#### Add a fragment via XML

To declaratively add a fragment to your activity layout's XML, use a `FragmentContainerView` element.

Here's an example activity layout containing a single `FragmentContainerView`:

```kotlin
<!-- res/layout/example_activity.xml -->
<androidx.fragment.app.FragmentContainerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/fragment_container_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:name="com.example.ExampleFragment" />
```

The `android:name` attribute specifies the class name of the `Fragment` to instantiate. When the activity's layout is inflated, the specified fragment is instantiated, [`onInflate()`](https://developer.android.com/reference/androidx/fragment/app/Fragment#onInflate%28android.content.Context,%2520android.util.AttributeSet,%2520android.os.Bundle%29) is called on the newly instantiated fragment, and a `FragmentTransaction` is created to add the fragment to the `FragmentManager`.

**Note:** You can use the `class` attribute instead of `android:name` as an alternative way to specify which `Fragment` to instantiate.

#### Add a fragment programmatically

To programmatically add a fragment to your activity's layout, the layout should include a `FragmentContainerView` to serve as a fragment container, as shown in the following example:

```kotlin
<!-- res/layout/example_activity.xml -->
<androidx.fragment.app.FragmentContainerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/fragment_container_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

Unlike the XML approach, the `android:name` attribute isn't used on the `FragmentContainerView` here, so no specific fragment is automatically instantiated. Instead, a [`FragmentTransaction`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction) is used to instantiate a fragment and add it to the activity's layout.

While your activity is running, you can make fragment transactions such as adding, removing, or replacing a fragment. In your `FragmentActivity`, you can get an instance of the [`FragmentManager`](https://developer.android.com/reference/androidx/fragment/app/FragmentManager), which can be used to create a `FragmentTransaction`. Then, you can instantiate your fragment within your activity's `onCreate()` method using [`FragmentTransaction.add()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#add%28int,%20java.lang.Class%3C?%20extends%20androidx.fragment.app.Fragment%3E,%20android.os.Bundle%29), passing in the `ViewGroup` ID of the container in your layout and the fragment class you want to add and then commit the transaction, as shown in the following example:


```kotlin
class ExampleActivity : AppCompatActivity(R.layout.example_activity) {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        if (savedInstanceState == null) {
            supportFragmentManager.commit {
                setReorderingAllowed(true)
                add<ExampleFragment>(R.id.fragment_container_view)
            }
        }
    }
}
```

**Note:** You should **always** use `setReorderingAllowed(true)` when performing a `FragmentTransaction`. For more information on reordered transactions, see [Fragment transactions](https://developer.android.com/guide/fragments/transactions#reordering).

In the previous example, note that the fragment transaction is only created when `savedInstanceState` is `null`. This is to ensure that the fragment is added only once, when the activity is first created. When a configuration change occurs and the activity is recreated, `savedInstanceState` is no longer `null`, and the fragment does not need to be added a second time, as the fragment is automatically restored from the `savedInstanceState`.

## Fragment manager

**Note:** We strongly recommend using the [Navigation library](https://developer.android.com/guide/navigation) to manage your app's navigation. The framework follows best practices for working with fragments, the back stack, and the fragment manager. For more information about Navigation, see [Get started with the Navigation component](https://developer.android.com/guide/navigation/navigation-getting-started) and [Migrate to the Navigation component](https://developer.android.com/guide/navigation/navigation-migrate).

[`FragmentManager`](https://developer.android.com/reference/androidx/fragment/app/FragmentManager) is the class responsible for performing actions on your app's fragments, such as adding, removing, or replacing them and adding them to the back stack.

**You might never interact with `FragmentManager` directly if you're using the [Jetpack Navigation](https://developer.android.com/guide/navigation) library, as it works with the `FragmentManager` on your behalf.** However, any app using fragments is using `FragmentManager` at some level, so it's important to understand what it is and how it works.

### Access the FragmentManager

You can access the `FragmentManager` from an activity or from a fragment.

[`FragmentActivity`](https://developer.android.com/reference/androidx/fragment/app/FragmentActivity) and its subclasses, such as [`AppCompatActivity`](https://developer.android.com/reference/androidx/appcompat/app/AppCompatActivity), have access to the `FragmentManager` through the [`getSupportFragmentManager()`](https://developer.android.com/reference/androidx/fragment/app/FragmentActivity#getSupportFragmentManager%28%29) method.

Fragments can host one or more child fragments. Inside a fragment, you can get a reference to the `FragmentManager` that manages the fragment's children through [`getChildFragmentManager()`](https://developer.android.com/reference/androidx/fragment/app/Fragment#getChildFragmentManager%28%29). If you need to access its host `FragmentManager`, you can use [`getParentFragmentManager()`](https://developer.android.com/reference/androidx/fragment/app/Fragment#getParentFragmentManager%28%29).

Here are a couple of examples to see the relationships between fragments, their hosts, and the `FragmentManager` instances associated with each.

![two ui layout examples showing the relationships between
            fragments and their host activities]({{site.baseurl}}/assets/images/fragment-host.png)


**Figure 1.** Two UI layout examples showing the relationships between fragments and their host activities.

Figure 1 shows two examples, each of which has a single activity host. The host activity in both of these examples displays top-level navigation to the user as a [`BottomNavigationView`](https://developer.android.com/reference/com/google/android/material/bottomnavigation/BottomNavigationView) that is responsible for swapping out the host fragment with different screens in the app. Each screen is implemented as a separate fragment.

The host fragment in Example 1 hosts two child fragments that make up a split-view screen. The host fragment in Example 2 hosts a single child fragment that makes up the display fragment of a [swipe view](https://developer.android.com/guide/navigation/navigation-swipe-view-2#implement_swipe_views).

Given this setup, you can think about each host as having a `FragmentManager` associated with it that manages its child fragments. This is illustrated in figure 2 along with property mappings between `supportFragmentManager`, `parentFragmentManager`, and `childFragmentManager`.

![each host has its own FragmentManager associated with it
            that manages its child fragments]({{site.baseurl}}/assets/images/manager-mappings.png)

**Figure 2.** Each host has its own `FragmentManager` associated with it that manages its child fragments.

The appropriate `FragmentManager` property to reference depends on where the callsite is in the fragment hierarchy along with which fragment manager you are trying to access.

Once you have a reference to the `FragmentManager`, you can use it to manipulate the fragments being displayed to the user.

### Child fragments

Generally speaking, your app consists of a single or small number of activities in your application project, with each activity representing a group of related screens. The activity might provide a point to place top-level navigation and a place to scope `ViewModel` objects and other view-state between fragments. A fragment represents an individual destination in your app.

If you want to show multiple fragments at once, such as in a split-view or a dashboard, you can use child fragments that are managed by your destination fragment and its child fragment manager.

Other use cases for child fragments are the following:

- [Screen slides](https://developer.android.com/training/animation/screen-slide-2), using a `ViewPager2` in a parent fragment to manage a series of child fragment views.
- Sub-navigation within a set of related screens.
- Jetpack Navigation uses child fragments as individual destinations. An activity hosts a single parent `NavHostFragment` and fills its space with different child destination fragments as users navigate through your app.

### Use the FragmentManager

The `FragmentManager` manages the fragment back stack. At runtime, the `FragmentManager` can perform back stack operations like adding or removing fragments in response to user interactions. Each set of changes is committed together as a single unit called a [`FragmentTransaction`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction). For a more in-depth discussion about fragment transactions, see the [fragment transactions guide](https://developer.android.com/guide/fragments/transactions).

When the user taps the Back button on their device, or when you call [`FragmentManager.popBackStack()`](https://developer.android.com/reference/androidx/fragment/app/FragmentManager#popBackStack%28%29), the top-most fragment transaction pops off of the stack. If there are no more fragment transactions on the stack, and if you aren't using child fragments, the Back event bubbles up to the activity. If you *are* using child fragments, see [special considerations for child and sibling fragments](#considerations).

When you call [`addToBackStack()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#addToBackStack%28java.lang.String%29) on a transaction, the transaction can include any number of operations, such as adding multiple fragments or replacing fragments in multiple containers.

When the back stack is popped, all these operations reverse as a single atomic action. However, if you committed additional transactions prior to the `popBackStack()` call, and if you *didn't* use `addToBackStack()` for the transaction, these operations *don't* reverse. Therefore, within a single `FragmentTransaction`, avoid interleaving transactions that affect the back stack with those that don't.

### Perform a transaction

To display a fragment within a layout container, use the `FragmentManager` to create a `FragmentTransaction`. Within the transaction, you can then perform an [`add()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#add%28int,%20java.lang.Class%3C?%20extends%20androidx.fragment.app.Fragment%3E,%20android.os.Bundle%29) or [`replace()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#replace%28int,%20java.lang.Class%3C?%20extends%20androidx.fragment.app.Fragment%3E,%20android.os.Bundle%29) operation on the container.

For example, a simple `FragmentTransaction` might look like this:

```kotlin
supportFragmentManager.commit {
   replace<ExampleFragment>(R.id.fragment_container)
   setReorderingAllowed(true)
   addToBackStack("name") // Name can be null
}
```

In this example, `ExampleFragment` replaces the fragment, if any, that is currently in the layout container identified by the `R.id.fragment_container` ID. Providing the fragment's class to the [`replace()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#replace%28int,%20java.lang.Class%3C?%20extends%20androidx.fragment.app.Fragment%3E,%20android.os.Bundle%29) method lets the `FragmentManager` handle instantiation using its [`FragmentFactory`](https://developer.android.com/reference/androidx/fragment/app/FragmentFactory). For more information, see the [Provide dependencies to your fragments](#dependencies) section.

[`setReorderingAllowed(true)`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#setReorderingAllowed%28boolean%29) optimizes the state changes of the fragments involved in the transaction so that animations and transitions work correctly. For more information on navigating with animations and transitions, see [Fragment transactions](https://developer.android.com/guide/fragments/transactions) and [Navigate between fragments using animations](https://developer.android.com/training/basics/fragments/animate).

Calling [`addToBackStack()`](https://developer.android.com/reference/androidx/fragment/app/FragmentTransaction#addToBackStack%28java.lang.String%29) commits the transaction to the back stack. The user can later reverse the transaction and bring back the previous fragment by tapping the Back button. If you added or removed multiple fragments within a single transaction, all those operations are undone when the back stack is popped. The optional name provided in the `addToBackStack()` call gives you the ability to pop back to a specific transaction using [`popBackStack()`](https://developer.android.com/reference/androidx/fragment/app/FragmentManager#popBackStack%28java.lang.String,%20int%29).

If you don't call `addToBackStack()` when you perform a transaction that removes a fragment, then the removed fragment is destroyed when the transaction is committed, and the user cannot navigate back to it. If you do call `addToBackStack()` when removing a fragment, then the fragment is only `STOPPED` and is later `RESUMED` when the user navigates back. Its view *is* destroyed in this case. For more information, see [Fragment lifecycle](https://developer.android.com/guide/fragments/lifecycle).

## FAQs

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

- https://developer.android.com/guide/fragments/create
- https://stackoverflow.com/questions/28929637/difference-and-uses-of-oncreate-oncreateview-and-onactivitycreated-in-fra
