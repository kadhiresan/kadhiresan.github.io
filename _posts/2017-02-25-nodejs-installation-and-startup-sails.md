---
layout: post
title: Node JS Installation and Setup the sails js project
---

**Node Js:**
Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world. - ([from nodejs.org!](https://nodejs.org/en/))

**Table of contents**

  1. Installing NodeJS and setup the sails on Local
  2. Installing NodeJS and setup the sails on AWS


**Installing NodeJS and setup the sails on Local**

  - We can download the Node.js source code or a pre-built installer for your platform, and start developing today from here ([Downloads](https://nodejs.org/en/download/)).
  - it's always better to download stable version of any software, i would suggest you do the same.


* Step 1
  - Download the you nodejs source code or pre-built installer for your platform
* Step 2
  - Install the node software you download from the above link
* Step 3
  - Make sure you have Node and NPM installed by running simple commands to see what version of each is installed and to run a simple test program
  - Open the terminal or any similar command line tool, and type below commands
  > node -v

  > npm -v
* Step 4
  - Install the Sails js globally

  ```
  
  $ npm install sails -g

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
**3.Arrays**

Array can hold more then one values of different data types..

  * creation using literal syntax

```javascript
//Bad
var foo = New Array();

//Good
var foo = []; //array literal
```
  * Array starts at index 0

```javascript
var bar = [1]; // array starts at index 0

console.log(bar[0]); //print 1
```
  * Add a new item to an array

```javascript
var bar = [1];
bar.push(2); //adds 2 at the end of an array

console.log(bar); //print [1, 2]
```
  * Add a new item at start of an array

```javascript
var bar = [1];
bar.unshift(2); //adds 2 before 1

console.log(bar); //print [2, 1]
```
  * Remove an item at start of an array

```javascript

var bar = [4, 1, 2];
bar.shift(); //removes 4 from the start

console.log(bar); //print [1, 2]
```
  * Remove an item at the end of an array

```javascript

var bar = [2, 1, 5];
bar.pop(); //removes 5 from the end

console.log(bar); //print [2, 1]
```
  * Get the length of an array

```javascript

var bar = [1, 2, 'hello'];

console.log(bar.length); //print 3
```

**4.Objects** ([Objects Overview](http://www.tutorialspoint.com/javascript/javascript_objects.htm))

Object creation using literal syntax

```javascript
//bad
var obj = new Object();

//good
var obj = {}; //empty object literal

  Accessing an object

var obj = {
  name: 'ABC',
  type: 'Alphabet',
  id: 123
};

console.log(obj.name); //print ABC

console.log(obj['name']); //print ABC
```
  * Use better naming convension and don't use reserved keywords such as private, class etc.

```javascript
//bad
var obj = {
  class: 'car'
};

//good
var obj = {
  type: 'car'
};
```
  * The this Keyword
**this** is not a variable. It is a keyword. You cannot change the value of this.

```javascript
function book(name, type, rating) {
  this.bookName = name;
  this.bookType = type;
  this.bookRating = eyratinge;
}
 var mybook_1 = new book("js", "programming", 4.5);
 var mybook_2 = new book("node.js", "programming", 4.7);
```
In the global execution context (outside of any function), this refers to the global object, whether in strict mode or not.

```javascript
console.log(this.document === document); // true

// In web browsers, the window object is also the global object:
console.log(this === window); // true

this.a = 37;
console.log(window.a); // 37
```

**5.Strings**
Using single quote '' for strings

```javascript
//bad
var bar = "Hello world";

//good
var bar = 'Hello world';
```

Using + to concatenate strings

```javascript
var bar = 'Hi i am ' + 'kadhir';
```

**6.Functions**

* Function declarations

```javascript
function funz(name) {
  alert('My name is ' + name); //will alert my name is kadhir
}

funz('kadhir'); //call's the above function with argument

var newFunz = new funz(); //creates an instance of the function funz
```

* Function expressions

```javascript
//anonymous function
var funz = function() {
  alert('I am a function too');
};

funz();
```

* Named function expression

```javascript
var namedFunz = function funz() {
  alert('I am a function too');
};

namedFunz();
```

*Immediately invoked function express (IIFE)
  - below function is called automatically

```javascript
(function () {
  alert('I am a function which is invoked automatically');
})();
```

**7.Variables**

* Variable creation

```javascript
//bad
foo = 1; //Stores 1 as global variable

//good
var foo = 1; //assigns number 1 to the variable foo
```

* Local and Global variables

```javascript
//global
var foo = 1; 

alert(foo); //will alert 1

function funz() {
  var bar = 10; //local variable
  console.log(bar); //print 10
  foo = 10; //changing the global variable value 1 to 10
}

funz(); //calling the function

alert(foo); //will alert 10
```

**8.Comparison Operators**

Always use === instead of == and !== instead of !=

Difference is that === and !== will also check the type of the variable, See below example

```javascript
var foo = 1;
 var bar = '1';

 console.log(bar == 1); //True, because `==` will do automatic type conversion

 console.log(bar === 1); //False, because 1 !== '1'

 console.log(bar === foo); //False

 console.log(bar !== foo); //True , '1' is not equal value as well as type
```

**9.Loops**

for, for/in, while, do/while loop

* for loop

```javascript
for (statement 1; statement 2; statement 3) {

}

//statement 1 - Executes before the loop
//statement 2 - Condition to run the loop
//statement 3 - Executes each time after the loop

//See below for example

for (var i = 0; i < 10; i++) {
  console.log(i); //Will print from 0 to 9
}
```

* for/in loop to loop through an array or object

```javascript
for (var x in array or object)  {

}

//Looping through an array
var foo = [1, 2, 3, 4, 5];

for (var i in foo) {
  console.log(foo[i]); //Will loop the array and prints 1 to 5
}

//Looping through an object
var obj = { fname : 'Kadhir', lname : 'kk'};

for (var name in obj) { 

  //To check property belongs to object, not to prototype object
  //hasOwnProperty is only to check objects

  if (obj.hasOwnProperty(name)) {
    console.log(obj[name]); //Will print "Kadhir" and "kk"
  }

}
```

* while loop

```javascript
while (statement 1) {

}

//statement 1 - Condition to run the loop
//See below for example

var i = 0;

while (i < 10) {
  i++; //Increment i
  console.log(i); //Will print from 1 to 10
}
```

* do/while loop will execute once, before checking the condition in while

```javascript
do {
  //Execute once before checking while condition
} while(statement 1)

//statement 1 - Condition to run the loop
//See below for example

var i = 0;

do {
  console.log(i); //Will print from 0 to 10
  i++; //Increment i
} while (i < 10) 
```

<code>Tips: dont use array.length in for loop, i mean you need to get the length of array value before loop start</code>

```javascript
var number = [1,2,3,4,5,6,7,8,9];
var len = number.length; //else .length will call each iteration
for (var i = 0; i < len; i++) { 
  //code
}
```
**10.Prototypes**

In javascript function, array, objects are considered as objects

All objects in js inherit, properties and methods from the prototype

```javascript
function person(name, age) {
  this.name = name;
  this.age  = age;
}

person.prototype.model = 'Car';

//model `car` is added to the person() from its prototype

var newPerson = new person('Kadhir', 23); //calling the person()

console.log(newPerson); //Will print {name: "Kadhir", age: 23, model: "Car"}
```


















