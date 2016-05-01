---
layout: post
title: JavaScript Basics and Guidelines
---

**Java Script:**
object-oriented computer programming language commonly used to create interactive effects within web browsers, and now a days js is not only for web other than that.

**Table of contents**

  1. Comments
  2. Types (Primitives)
  3. Arrays
  4. Objects and this
  5. Strings
  6. Functions
  7. Variables
  8. Conditional Statements
  9. Comparison Operators
  10. Loops
  11. Prototypes

**Comments**

Comments: In javascript there are 2 types of comments
* Single line comment

* Multi line comment

```javascript
//this is a single line comment

/*
  this is a multi line comment
*/
```

**DataTypes**

1.Primitive data types:

* number
* string
* boolean (true or false)
* undefined
* null

```javascript
var foo = 1; //number
var bar = 'Hello World'; //string
```

Above primitive data type values are accessed directly without any reference.

2.Other datatypes: such as object, array are accessed by its reference

* object
* array

```javascript
var foo = [1, 'hello']; //array

foo[0] = 1; //accessing array value by its reference

var bar = {
  name: 'Hello World' 
}; //object

bar.name = 'Hello World'; //accessing object by its reference
```
An example for String

```javascript
function stringFunz(str) {
  str = 'bar';
}

var string = 'foo';
console.log(string); // "foo"

stringFunz(string);
console.log(string); // "foo"

//Above string still remains as 'foo'
```

Now let's try it with a reference in object

```javascript
function objectFunz(obj) {
  obj.name = 'bar';
}

var obj = {}; //New object

obj.name = 'foo';
console.log(obj.name); // "foo"

objectFunz(object);
console.log(obj.name); // "bar"

//See now the obj.name is changed to 'bar'
```





