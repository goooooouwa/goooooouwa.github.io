---
title: Android编程笔记（七）：ViewModel & LiveData
category: coding
tags: android live-data view-model
published: true
---
## How to use ViewModel

### 0. 安装ViewModel, LiveData和其他Lifecycle依赖

Note: To import Lifecycle (including ViewModel & LiveData) into your Android project, see the instructions for declaring dependencies in the Lifecycle [release notes](https://developer.android.com/jetpack/androidx/releases/lifecycle#declaring_dependencies).

Add the dependencies for the artifacts you need in the build.gradle file for your app or module:

```kotlin
dependencies {
        val lifecycle_version = "2.9.1"
        val arch_version = "2.2.0"

        // ViewModel
        implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:$lifecycle_version")
        // ViewModel utilities for Compose
        implementation("androidx.lifecycle:lifecycle-viewmodel-compose:$lifecycle_version")
        // LiveData
        implementation("androidx.lifecycle:lifecycle-livedata-ktx:$lifecycle_version")
        // Lifecycles only (without ViewModel or LiveData)
        implementation("androidx.lifecycle:lifecycle-runtime-ktx:$lifecycle_version")
        // Lifecycle utilities for Compose
        implementation("androidx.lifecycle:lifecycle-runtime-compose:$lifecycle_version")

        // Saved state module for ViewModel
        implementation("androidx.lifecycle:lifecycle-viewmodel-savedstate:$lifecycle_version")

        // ViewModel integration with Navigation3
        implementation("androidx.lifecycle:lifecycle-viewmodel-navigation3:1.0.0-alpha02")

        // Annotation processor
        kapt("androidx.lifecycle:lifecycle-compiler:$lifecycle_version")
        // alternately - if using Java8, use the following instead of lifecycle-compiler
        implementation("androidx.lifecycle:lifecycle-common-java8:$lifecycle_version")
```

### 1. How to create a view model

```kotlin
import androidx.lifecycle.ViewModel

class MyViewModel : ViewModel() {
    // Your ViewModel logic here
}
```

### 2. How to access a view model

To access a ViewModel, you use the `viewModels()` extension functions (for Fragments and Activities) provided by the `androidx.activity` library. This function retrieve a `ViewModel` instance scoped to the `ViewModelStoreOwner` (Activity, Fragment, or Navigation destination). 

```kotlin
import androidx.activity.viewModels

class DiceRollActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        // Create a ViewModel the first time the system calls an activity's onCreate() method.
        // Re-created activities receive the same DiceRollViewModel instance created by the first activity.

        // Use the 'by viewModels()' Kotlin property delegate
        // from the activity-ktx artifact
        val myViewModel: MyViewModel by viewModels()
        // Now you can access myViewModel
    }
}
```

#### Kotlin `by` keyword

The Kotlin soft keyword `by` is to:

- [delegates the implementation of an interface to another object.](https://kotlinlang.org/docs/delegation.html)
- [delegates the implementation of the accessors for a property to another object.](https://kotlinlang.org/docs/delegated-properties.html)

## The lifecycle of a ViewModel

The lifecycle of a [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel) is tied directly to its scope. A `ViewModel` remains in memory until the [`ViewModelStoreOwner`](https://developer.android.com/reference/kotlin/androidx/lifecycle/ViewModelStoreOwner) to which it is scoped disappears. This may occur in the following contexts:

- In the case of an activity, when it finishes.
- In the case of a fragment, when it detaches.
- In the case of a Navigation entry, when it's removed from the back stack.

This makes ViewModels a great solution for storing data that survives configuration changes.

Figure 1 illustrates the various lifecycle states of an activity as it undergoes a rotation and then is finished. The illustration also shows the lifetime of the [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel) next to the associated activity lifecycle. This particular diagram illustrates the states of an activity. The same basic states apply to the lifecycle of a fragment.

![Illustrates the lifecycle of a ViewModel as an activity changes state.]({{site.baseurl}}/assets/images/viewmodel-lifecycle.png)


You usually request a [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel) the first time the system calls an activity object's [`onCreate()`](https://developer.android.com/reference/android/app/Activity#onCreate%28android.os.Bundle%29) method. The system may call [`onCreate()`](https://developer.android.com/reference/android/app/Activity#onCreate%28android.os.Bundle%29) several times throughout the existence of an activity, such as when a device screen is rotated. The [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel) exists from when you first request a [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel) until the activity is finished and destroyed.

## ViewModel benefits

The key benefits of the ViewModel class are essentially two:

- It allows you to persist UI state.
- It provides access to business logic.

### Persistence

ViewModel allows persistence through both the state that a ViewModel holds, and the operations that a ViewModel triggers. This caching means that you don’t have to fetch data again through common configuration changes, such as a screen rotation.

#### Scope

When you instantiate a ViewModel, you pass it an object that implements the [`ViewModelStoreOwner`](https://developer.android.com/reference/kotlin/androidx/lifecycle/ViewModelStoreOwner) interface. This may be a Navigation destination, Navigation graph, activity, fragment, or any other type that implements the interface. Your ViewModel is then scoped to the [Lifecycle](https://developer.android.com/reference/androidx/lifecycle/Lifecycle) of the `ViewModelStoreOwner`. It remains in memory until its `ViewModelStoreOwner` goes away permanently.

A range of classes are either direct or indirect subclasses of the `ViewModelStoreOwner` interface. The direct subclasses are [`ComponentActivity`](https://developer.android.com/reference/androidx/activity/ComponentActivity), [`Fragment`](https://developer.android.com/reference/androidx/fragment/app/Fragment), and [`NavBackStackEntry`](https://developer.android.com/reference/androidx/navigation/NavBackStackEntry). For a full list of indirect subclasses, see the [`ViewModelStoreOwner` reference](https://developer.android.com/reference/kotlin/androidx/lifecycle/ViewModelStoreOwner).

When the fragment or activity to which the ViewModel is scoped is destroyed, asynchronous work continues in the ViewModel that is scoped to it. This is the key to persistence.

For more information, see the section below on [ViewModel lifecycle](#lifecycle).

#### SavedStateHandle

[SavedStateHandle](https://developer.android.com/topic/libraries/architecture/viewmodel/viewmodel-savedstate) allows you to persist data not just through configuration changes, but across process recreation. That is, it enables you to keep the UI state intact even when the user closes the app and opens it at a later time.

### Access to business logic

Even though the vast majority of [business logic](https://developer.android.com/topic/architecture/ui-layer/stateholders#business-logic) is present in the data layer, the UI layer can also contain business logic. This can be the case when combining data from multiple repositories to create the screen UI state, or when a particular type of data doesn't require a data layer.

ViewModel is the right place to handle business logic in the UI layer. The ViewModel is also in charge of handling events and delegating them to other layers of the hierarchy when business logic needs to be applied to modify application data.

## Referencces

- https://developer.android.com/topic/libraries/architecture/viewmodel
- https://developer.android.com/jetpack/androidx/releases/lifecycle#declaring_dependencies
- https://developer.android.com/topic/libraries/architecture/livedata
