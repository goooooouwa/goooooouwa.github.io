---
title: Android编程笔记（一）：Model
category: coding
tags: android db model kotlin coroutine
published: true
---

* TOC
{:toc}

## 如何在Android应用中创建和使用数据库

### 0. 安装Room依赖

将以下依赖项添加到应用的 build.gradle 文件。

注意 ：请仅选择 ksp 或 annotationProcessor 中的一项。请勿同时包含这两项。

```kotlin
dependencies {
    val room_version = "2.7.1"

    implementation("androidx.room:room-runtime:$room_version")

    // If this project uses any Kotlin source, use Kotlin Symbol Processing (KSP)
    // See Add the KSP plugin to your project
    ksp("androidx.room:room-compiler:$room_version")

    // If this project only uses Java source, use the Java annotationProcessor
    // No additional plugins are necessary
    annotationProcessor("androidx.room:room-compiler:$room_version")

    // optional - Kotlin Extensions and Coroutines support for Room
    implementation("androidx.room:room-ktx:$room_version")

    // optional - RxJava2 support for Room
    implementation("androidx.room:room-rxjava2:$room_version")

    // optional - RxJava3 support for Room
    implementation("androidx.room:room-rxjava3:$room_version")

    // optional - Guava support for Room, including Optional and ListenableFuture
    implementation("androidx.room:room-guava:$room_version")

    // optional - Test helpers
    testImplementation("androidx.room:room-testing:$room_version")

    // optional - Paging 3 Integration
    implementation("androidx.room:room-paging:$room_version")
}
```

#### 0.1 将 KSP 插件添加到您的项目中

首先，在顶级 `build.gradle.kts` 文件中声明 KSP 插件。请务必选择与项目的 Kotlin 版本一致的 KSP 版本。您可以在 KSP GitHub 页面上找到版本列表。

注意 ：KSP 版本的前一部分必须与 build 中使用的 Kotlin 版本一致。例如，如果您使用的是 Kotlin 2.0.21，则 KSP 版本必须是 2.0.21-x.y.z 版本之一。可以在`libs.versions.toml`文件中查看当前项目使用的Kotlin的版本。

```kotlin
plugins {
    id("com.google.devtools.ksp") version "2.0.21-1.0.27" apply false
}
```

然后，在模块级 build.gradle.kts 文件中启用 KSP：

```kotlin
plugins {
    id("com.google.devtools.ksp")
}
```

### 1. 创建Entity, Dao和Database类

#### 1.1 创建Entity数据实体类

使用`@Entity` annotation来创建数据实体类。每个数据实体类有一个或多个Primary Key，通过`@PrimaryKey` annotation来标识。Room默然会根据参数名来匹配数据表的列名，你可以通过`@ColumnInfo` annotation来自定义数据列的属性。

You define each Room entity as a class annotated with `@Entity`. A Room entity includes fields for each column in the corresponding table in the database, including one or more columns that make up the primary key.

By default, Room uses the class name as the database table name. If you want the table to have a different name, set the tableName property of the `@Entity` annotation. Similarly, Room uses the field names as column names in the database by default. If you want a column to have a different name, add the `@ColumnInfo` annotation to the field and set the name property. 

```kotlin
@Entity
data class Student(
	@PrimaryKey(autoGenerate=true)
	@ColumnInfo(name="student_id")
	var studentId: Int,

	@ColumnInfo(name="student_name")
	var studentName: String,

	@ColumnInfo(name="student_email")
	var studentEmail: String
)
```

#### 1.2 创建Dao接口

使用`@Dao` annotation来创建Dao接口或者抽象类。

You can define each DAO as either an interface or an abstract class. For basic use cases, you usually use an interface. In either case, you must always annotate your DAOs with `@Dao`. DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database.

Dao提供了各种基础的数据访问方法。所有对数据进行操作的方法（如Insert, Update, Delete）都只接受一个或多个Entity数据类作为参数。

Each parameter for an `@Insert` method must be either an instance of a [Room data entity class](https://developer.android.com/training/data-storage/room/defining-data) annotated with `@Entity` or a collection of data entity class instances, each of which points to a database. 

All of the parameters of the Insert method must either be classes annotated with `Entity` or collections/array of it.

使用`@Query` annotation可以创建自定义SQL语句来进行数据查询或者更加复杂的数据操作，并将其封装成Dao方法以供调用。

The `@Query` annotation lets you write SQL statements and expose them as DAO methods. Use these query methods to query data from your app's database or when you need to perform more complex insertions, updates, and deletions.

```kotlin
@Dao
interface StudentDao {
    @Insert
    fun createStudent(vararg students: Student)

    @Update
    fun createStudent(vararg students: Student)

    @Delete
    fun createStudent(vararg students: Student)

    @Query("SELECT * FROM student")
    fun getAllStudents(): List<Student>

    @Query("SELECT * from student WHERE student_name = :name LIMIT 1")
    fun findStudentByName(name: String): Student
}
```

`vararg` Kotlin语法允许调用者传入可变数量的某一类型参数而无需提前构造集合类（如数组）。

In Kotlin, `vararg` allows a function to accept a variable number of arguments of the same type. It simplifies function calls by eliminating the need to create collections when passing multiple values.

```kotlin
fun printNames(vararg names: String) {
    names.forEach { name -> println(name) }
}

fun main() {
    printNames("Alice", "Bob", "Charlie")
    // Output:
    // Alice
    // Bob
    // Charlie
    
    val people = arrayOf("David", "Eve")
    printNames(*people) // Using spread operator to pass an array as vararg
    // Output:
    // David
    // Eve
}
```

Dao方法允许以此方式批量创建、修改和删除多条数据记录。比如，可以批量创建多条student记录：
```kotlin
createStudent(
	Student(0,"Alice","alice@gmail.com"),
	Student(0,"Bob","bob@gmail.com")
)
```

#### 1.3 创建Database类

创建Database类需要使用`@Database` annotation，并且在entities参数中提供所有与该数据库有关的Entity数据类。

The database class must satisfy the following conditions:

- The class must be annotated with a `@Database` annotation that includes an entities array that lists all of the data entities associated with the database.
- The class must be an abstract class that extends RoomDatabase.
- For each DAO class that is associated with the database, the database class must define an abstract method that has zero arguments and returns an instance of the DAO class.

```kotlin
@Database(entities=[Student::class], version=1)
abstract class StudentDatabase: RoomDatabase() {
	abstract fun studentDao(): StudentDao
}
```

### 2. 使用Singleton模式访问Database实例

使用Kotlin提供的companion object可以轻松创建类方法和属性，可以用来实现Singleton模式，用于模式访问Database实例。

Companion objects allow you to define class-level functions and properties. This makes it easy to create factory methods, hold constants, and access shared utilities.

创建新项目时，直接将以下模板代码拷贝到项目中进行简答修改即可用来访问Database实例。

```kotlin
@Database(entities = [Student::class], version = 1)
abstract class StudentDatabase: RoomDatabase() {
    abstract fun studentDao(): StudentDao

    companion object{
        @Volatile
        private var INSTANCE: StudentDatabase? = null

        fun getInstance(context: Context): StudentDatabase {
            synchronized(this){
                var instance = INSTANCE

                if(instance == null){
                    instance = Room.databaseBuilder(
                        context.applicationContext,
                        StudentDatabase::class.java,
                        "students_database"
                    ).build()
                }
                return instance
            }
        }
    }
}
```

Android app会在数据库初始化时自动根据Entities和Database创建SQLite数据库和数据表。(有待验证)

### 3. 访问Dao对象

使用以下方法访问Dao对象

```kotlin
val studentDao = StudentDatabase.getInstance(application).studentDao()
```

### 4. UI thread & Worker threads

In Android, the UI thread, also known as the main thread, is responsible for handling all UI-related operations and user interactions. Therefore, **long-running or blocking operations** should not be executed on the UI thread to prevent the application from freezing and becoming unresponsive, which can lead to an "Application Not Responding" (ANR) error. 

Here's a more detailed explanation:

- **UI Thread Responsibilities:**

The UI thread is crucial for rendering the user interface, processing user input (like touch events and button clicks), and managing the lifecycle of UI components.

- **Concurrency Issues:**

Android's UI toolkit is not thread-safe, meaning that only the UI thread should directly interact with UI elements. Modifying UI components from other threads can lead to unpredictable behavior and crashes.

- **Consequences of Blocking the UI Thread:**

If the UI thread is blocked for an extended period (typically more than 5 seconds), the system will display an ANR dialog to the user, indicating that the application is not responding.

- **Best Practices:**

To avoid blocking the UI thread, long-running tasks like network requests, database operations, or complex calculations should be offloaded to background threads (also called worker threads).

- **Updating the UI from Background Threads:**

After completing a task in a background thread, the results need to be posted back to the UI thread to update the UI safely. This can be achieved using mechanisms like `runOnUiThread()`, `Handlers`, or `View.post()`, or using modern concurrency APIs like `AsyncTask` or `Kotlin Coroutines`.

In essence, the UI thread should be kept responsive and free from intensive operations to ensure a smooth and efficient user experience.

### 5. Kotlin Coroutines

Kotlin Coroutines是用来管理多线程计算的语法工具。Coroutine里的代码在默认情况下跟普通代码一样，是线性执行的，外层代码不用显式等待Coroutine里的代码在其他线程运算结果的完成（详情见下文Sequential by default）；而如果希望Coroutine里的代码能够并行执行(Concurrency)，则可通过`async` & `await`语法实现（详情见下文Concurrent using async）。

Kotlin provides only minimal low-level APIs in its standard library to enable other libraries to utilize coroutines. Unlike many other languages with similar capabilities, async and await are not keywords in Kotlin and are not even part of its standard library. Moreover, **Kotlin's concept of suspending function provides a safer and less error-prone abstraction for asynchronous operations than futures and promises.**

`kotlinx.coroutines` is a rich library for coroutines developed by JetBrains. It contains a number of high-level coroutine-enabled primitives, including `launch`, `async`, and others.

#### What is a suspending function

A suspending function is simply a function that can be paused and resumed at a later time. They can execute a long running operation and wait for it to complete without blocking.

The syntax of a suspending function is similar to that of a regular function except for the addition of the suspend keyword. It can take a parameter and have a return type. However, suspending functions can only be invoked by another suspending function or within a coroutine.

```kotlin
suspend fun backgroundTask(param: Int): Int {
     // long running operation
}
```

#### Sequential by default

Assume that we have two suspending functions defined elsewhere that do something useful like some kind of remote service call or computation. We just pretend they are useful, but actually each one just delays for a second for the purpose of this example:

```kotlin
suspend fun doSomethingUsefulOne(): Int {
    delay(1000L) // pretend we are doing something useful here
    return 13
}

suspend fun doSomethingUsefulTwo(): Int {
    delay(1000L) // pretend we are doing something useful here, too
    return 29
}
```

What do we do if we need them to be invoked **sequentially** — first `doSomethingUsefulOne` **and then** `doSomethingUsefulTwo`, and compute the sum of their results? In practice, we do this if we use the result of the first function to make a decision on whether we need to invoke the second one or to decide on how to invoke it.

We use a normal sequential invocation, because the code in the coroutine, just like in the regular code, is **sequential** by default. The following example demonstrates it by measuring the total time it takes to execute both suspending functions:

```kotlin
val time = measureTimeMillis {
    val one = doSomethingUsefulOne()
    val two = doSomethingUsefulTwo()
    println("The answer is ${one + two}")
}
println("Completed in $time ms")
```

It produces something like this:

```
The answer is 42
Completed in 2017 ms
```

#### Concurrent using async

What if there are no dependencies between invocations of `doSomethingUsefulOne` and `doSomethingUsefulTwo` and we want to get the answer faster, by doing both **concurrently**? This is where [async](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/async.html) comes to help.

Conceptually, [async](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/async.html) is just like [launch](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/launch.html). It starts a separate coroutine which is a light-weight thread that works concurrently with all the other coroutines. The difference is that `launch` returns a [Job](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-job/index.html) and does not carry any resulting value, while `async` returns a [Deferred](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-deferred/index.html) — a light-weight non-blocking future that represents a promise to provide a result later. You can use `.await()` on a deferred value to get its eventual result, but `Deferred` is also a `Job`, so you can cancel it if needed.

```kotlin
val time = measureTimeMillis {
    val one = async(start = CoroutineStart.LAZY) { doSomethingUsefulOne() }
    val two = async(start = CoroutineStart.LAZY) { doSomethingUsefulTwo() }
    // some computation
    one.start() // start the first one
    two.start() // start the second one
    println("The answer is ${one.await() + two.await()}")
}
println("Completed in $time ms")
```

It produces something like this:

```
The answer is 42
Completed in 1017 ms
```

This is twice as fast, because the two coroutines execute concurrently. Note that concurrency with coroutines is always explicit.

#### Coroutine的实例和语法解释

```kotlin
fun main() = runBlocking { // this: CoroutineScope
    launch { doWorld() }
    println("Hello")
}

// this is your first suspending function
suspend fun doWorld() {
    delay(1000L)
    println("World!")
}
```

`launch` is a coroutine builder. It launches a new coroutine concurrently with the rest of the code, which continues to work independently. That's why Hello has been printed first.

`runBlocking` is also a coroutine builder that bridges the non-coroutine world of a regular fun main() and the code with coroutines inside of `runBlocking { ... }` curly braces. This is highlighted in an IDE by `this: CoroutineScope` hint right after the runBlocking opening curly brace.

`suspend` a suspending function, which is simply a function that can be paused and resumed at a later time. **Suspending functions can only be invoked by another suspending function or within a coroutine.**

`delay` is a special suspending function. It suspends the coroutine for a specific time. Suspending a coroutine does not block the underlying thread, but allows other coroutines to run and use the underlying thread for their code.

`async` creates a coroutine and returns its future result as an implementation of Deferred. The running coroutine is cancelled when the resulting deferred is cancelled. Conceptually, `async` is just like `launch`. It starts a separate coroutine which is a light-weight thread that works concurrently with all the other coroutines. The difference is that `launch` returns a Job and does not carry any resulting value, while `async` returns a `Deferred` — a light-weight non-blocking future that represents a promise to provide a result later.

`await` you can use `.await()` on a deferred value to get its eventual result, but `Deferred` is also a Job, so you can cancel it if needed.

`Deferred` Deferred value is a non-blocking cancellable future — it is a Job with a result.

`Job` a background job. Conceptually, a job is a cancellable thing with a lifecycle that concludes in its completion.


### 6. 如何在UI中进行数据库操作

在Android app中数据库操作需要在非UI thread进行，以避免阻塞UI渲染。使用Kotlin Coroutine可以轻松在不同thread间允许异步代码。

在UI thread中可以使用`CoroutineScope`来启动Coroutine，比如：

```kotlin
button.setOnClickListener {
    // Create a new coroutine to move the execution off the UI thread
    CoroutineScope(Dispatchers.IO).launch {
        ...
    }
}
```

### 7. 在ViewModel中进行数据库操作

ViewModel includes a set of KTX extensions that work directly with coroutines. These extension are `lifecycle-viewmodel-ktx` library.

在ViewModel中可以使用其自带的Coroutine Scope `viewModelScope`来启动Coroutine，具体语法如下：

```kotlin
class StudentViewModel(
	private val dao:StudentDao
): ViewModel() {

    fun insertStudent(student: Student) {
        // Create a new coroutine to move the execution off the UI thread
        viewModelScope.launch(Dispatchers.IO) {
            dao.insertStudent(student)   // suspend function
        }
    }
}
```

Let's dissect the coroutines code in the `insertStudent` function:

- `viewModelScope` is a predefined CoroutineScope that is included with the ViewModel KTX extensions. Note that all coroutines must run in a scope. A CoroutineScope manages one or more related coroutines.
- `launch` is a function that creates a coroutine and dispatches the execution of its function body to the corresponding dispatcher.
- `Dispatchers.IO` indicates that this coroutine should be executed on a thread reserved for I/O operations.

Since this coroutine is started with viewModelScope, it is executed in the scope of the ViewModel. If the ViewModel is destroyed because the user is navigating away from the screen, viewModelScope is automatically cancelled, and all running coroutines are canceled as well.

## References:

- https://developer.android.com/training/data-storage/room
- https://developer.android.com/training/data-storage/room/accessing-data
- https://kotlinlang.org/docs/functions.html#variable-number-of-arguments-varargs
- https://stackoverflow.com/questions/40398072/singleton-with-parameter-in-kotlin
- https://kotlinlang.org/docs/coroutines-basics.html
- https://developer.android.com/topic/libraries/architecture/coroutines
- https://kotlinlang.org/docs/composing-suspending-functions.html
- https://stackoverflow.com/questions/47871868/what-does-the-suspend-function-mean-in-a-kotlin-coroutine
- https://developer.android.com/guide/components/processes-and-threads
