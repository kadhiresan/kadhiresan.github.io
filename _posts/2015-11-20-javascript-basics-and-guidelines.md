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

**1.Comments**

Comments: In javascript there are 2 types of comments

* Single line comment
* Multi line comment

```javascript
//this is a single line comment

/*
  this is a multi line comment
*/
```

**2.DataTypes**

* Primitive data types:
  - number
  - string
  - boolean (true or false)
  - undefined
  - null

```javascript
var foo = 1; //number
 var bar = 'Hello World'; //string
 var a; // a is undefined (check what is the diff between undefined and null in js)
```

Above primitive data type values are accessed directly without any reference.

* Other datatypes: such as **object, array** are accessed by its reference
  - object
  - array

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
function stringFunz(string) {
  string = 'bar';
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

 objectFunz(obj);
 console.log(obj.name); // "bar"

//See now the obj.name is changed to 'bar'
```
3.Arrays
Array can hold more then one variable with deffirent data dypes.
* creation using literal syntax

```javascript
//Bad
var foo = New Array();

//Good
var foo = []; //array literal
```
- Array starts at index 0
```javascript
var bar = [1]; // array starts at index 0

console.log(bar[0]); //print 1
```
- Add a new item to an array
```javascript
var bar = [1];
bar.push(2); //adds 2 at the end of an array

console.log(bar); //print [1, 2]
```
- Add a new item at start of an array
```javascript
var bar = [1];
bar.unshift(2); //adds 2 before 1

console.log(bar); //print [2, 1]
```
- Remove an item at start of an array
```javascript
var bar = [4, 1, 2];
bar.shift(); //removes 4 from the start

console.log(bar); //print [1, 2]
```
- Remove an item at the end of an array
```javascript
var bar = [2, 1, 5];
bar.pop(); //removes 5 from the end

console.log(bar); //print [2, 1]
```
- Get the length of an array
```javascript
var bar = [1, 2, 'hello'];

console.log(bar.length); //print 3
```







