---
title: JS prototype-based OOP key steps
category: coding
tags: javascript OOP
published: true
---

```
// 1. define the Person Class
function Person() {
    // constructor
}
Person.prototype.walk = function(){  alert ('I am walking!');};
Person.prototype.sayHello = function(){  alert ('hello');};

// 2. define the Student class
function Student() {
 // Call the parent constructor
  Person.call(this);
}

// 3. inherit Person
Student.prototype = new Person();

// 4. correct the constructor pointer because it points to Person
Student.prototype.constructor = Student;
```

## example of prototype chain

```
var s  = new Student();
s.__proto__ === Student.prototype   //true
Student.prototype.__proto__ === Person.prototype   //true
Person.prototype.__proto__ === Object.prototype    //true
Object.prototype.__proto__ === null    //true
```

s的原型链：Student.prototype —> Person.prototype —> Object.prototype —> null

so Student, Person and Object are just constructor functions, will not be present in the prototype chain at all.
