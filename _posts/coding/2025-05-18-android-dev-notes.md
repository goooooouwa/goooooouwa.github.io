---
title: Android编程笔记
category: coding
tags: android
published: true
---

## 如何在Android应用中创建和使用数据库

1. 创建Entity, Dao和Database类
2. 使用Singleton模式访问Database实例
3. 访问Dao对象
4. 在UI中进行数据库操作
5. 在ViewModel中进行数据库操作

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

        fun getInstance(context: Android app会在数据库初始化时自动根据Entities和Database创建SQLite数据库和数据表。Context): StudentDatabase {
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

### 4. 在UI中进行数据库操作

因此在Android app中数据库操作需要在非UI thread进行，使用Kotlin Coroutine可以轻松在不同thread间允许异步代码。

#### 4.1 Kotlin Coroutine语法

Coroutine的简单例子：

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

`delay` is a special suspending function. It suspends the coroutine for a specific time. Suspending a coroutine does not block the underlying thread, but allows other coroutines to run and use the underlying thread for their code.

`runBlocking` is also a coroutine builder that bridges the non-coroutine world of a regular fun main() and the code with coroutines inside of `runBlocking { ... }` curly braces. This is highlighted in an IDE by `this: CoroutineScope` hint right after the runBlocking opening curly brace.

Suspending functions can be used inside coroutines just like regular functions, but their additional feature is that they can, in turn, use other suspending functions (like delay in this example) to suspend execution of a coroutine.

#### 4.2 在UI中进行数据库操作

在UI thread中可以使用`CoroutineScope`来启动Coroutine，比如：

```kotlin
	button.setOnClickListener {
		// Create a new coroutine to move the execution off the UI thread
		CoroutineScope(Dispatchers.IO).launch {
		    ...
		}
	}
```

### 5. 在ViewModel中进行数据库操作

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
