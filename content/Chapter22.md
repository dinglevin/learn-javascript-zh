# 第二十二章·面试问题

This chapter discusses various questions to better prepare candidate on their understanding about JavaScript. It is divided into three parts: basic, intermediate and advance level.

* [Basic Level](./basic-level.md)
* [Intermediate Level](./intermediate-level.md)
* [Advance Level](./advance-level.md)

# Basic JavaScript Interview Questions

## 1. History and Defining Variables.

### 1.1. What is JavaScript?

**Answer:**
JavaScript is a high-level, interpreted programming language commonly used for web development to add interactivity and dynamic behavior to websites.

### 1.2. Who created/Developed JavaScript?

**Answer:**
JavaScript was created by _Brendan Eich_ while he was working at **Netscape Communications Corporation**. He developed the language in just ten days in May 1995. JavaScript was originally called "_Mocha_" but was later renamed "_LiveScript_" and eventually "_JavaScript_" as part of a marketing collaboration with **Sun Microsystems** (now **Oracle Corporation**), which had a programming language called **Java** that was gaining popularity at the time. Despite the name similarity, _JavaScript_ and _Java_ are entirely different programming languages with distinct purposes and characteristics.

### 1.3. How do you declare a variable in JavaScript?

**Answer:**
You can declare a variable using `var`, `let`, or `const`:

- `var` (function-scoped)
- `let` (block-scoped)
- `const` (block-scoped, for constants)

### 1.4. What is the difference between `let`, `var`, and `const`?

**Answer:**

- `var` is function-scoped, while `let` and `const` are block-scoped.
- `let` allows variable reassignment, while `const` is used for constants.
- Variables declared with `var` are hoisted, whereas `let` and `const` are not hoisted.

### 1.5. Is javascript a statically typed or a dynamically typed language?

**Answer:**
JavaScript is a dynamically typed language. In a dynamically typed language, the type of a variable is checked during run-time in contrast to a statically typed language, where the type of a variable is checked during compile-time.

| Feature | Static Typing | Dynamic Typing |
|---|---|---|
| Variables have types | Yes | No |
| Values have types | Yes | Yes |
| Variables can change type | No | Yes |
| Variables can change type dramatically | No | Yes |

Since javascript is a _loosely(dynamically)_ typed language, variables in JS are not associated with any type. A variable can hold the value of any data type.

For example, a variable that is assigned a number type can be converted to a string type:

```js
var a = 23;
var a = "Hello World!";
```

### 1.6. What are the types of errors in javascript?

**Answer:**
There are seven types of errors in javascript.

1. **Syntax error** - The error occurs when you use a predefined syntax incorrectly.
```js
const func = () =>
console.log(hello)
}
```
2. **Reference Error** - In a case where a variable reference can't be found or hasn't been declared, then a Reference error occurs.
```js
console.log(x);
```
3. **Type Error** - An error occurs when a value is used outside the scope of its data type.
```js
let num = 15;
console.log(num.split(""));
```
4. **Evaluation Error** - Current JavaScript engines and EcmaScript specifications do not throw this error. However, it is still available for backward compatibility. The error is called when the `eval()` backward function is used, as shown in the following code block

```js
try{
  throw new EvalError("'Throws an error'")
}catch(error){
  console.log(error.name, error.message)
}
```
5. **RangeError** - There is an error when a range of expected values is required.

```js
const checkRange = (num)=>{
  if (num < 30) throw new RangeError("Wrong number");
  return true
}

checkRange(20);
```
6. **URI Error** - When the wrong character(s) are used in a URI function, the error is called uri error
```js
console.log(decodeURI("https://www.educative.io/shoteditor"))
console.log(decodeURI("%sdfk"));
```
7. **Internal Error** - In the JS engine, this error occurs most often when there is too much data and the stack exceeds its critical size. When there are too many recursion patterns, switch cases, etc., the JS engine gets overwhelmed.
```js
switch(condition) {
 case 1:
 ...
 break
 case 2:
 ...
 break
 case 3:
 ...
 break
 case 4:
 ...
 break
 case 5:
 ...
 break
 case 6:
 ...
 break
 case 7:
 ...
 break
 ... up to 500 cases
 }
```

### 1.7. Mention some advantages of javascript.

**Answer:**
There are many advantages of javascript. Some of them are

- Javascript is executed on the client-side as well as server-side also. There are a variety of Frontend Frameworks that you may study and utilize. However, if you want to use JavaScript on the backend, you'll need to learn NodeJS. It is currently the only JavaScript framework that may be used on the backend.
- Javascript is a simple language to learn.
- Web pages now have more functionality because of Javascript.
- To the end-user, Javascript is quite quick.

### 1.8. What is the `this` keyword in JavaScript? 

**Answer:** The Keyword `this` in JavaScript is used to call the current object as a constructor to assign values to object properties.

## 2. Functions

### 2.1. How do you create a function in JavaScript?

**Answer:** You can create a function using the `function` keyword or arrow functions (`=>`):
**Example**:

```js
function myFunction() {
  // Function body
}

const myArrowFunction = () => {
  // Function body
};
```

### 2.2. What are Callbacks?

**Answer:**
A callback is a function that will be executed after another function gets executed. In javascript, functions are treated as first-class citizens, they can be used as an argument of another function, can be returned by another function, and can be used as a property of an object.

Functions that are used as an argument to another function are called callback functions.

**Example**:

```js
function divideByHalf(sum) {
  console.log(Math.floor(sum / 2));
}

function multiplyBy2(sum) {
  console.log(sum * 2);
}

function operationOnSum(num1, num2, operation) {
  var sum = num1 + num2;
  operation(sum);
}

operationOnSum(3, 3, divideByHalf); // Outputs 3

operationOnSum(5, 5, multiplyBy2); // Outputs 20
```

- In the code above, we are performing mathematical operations on the sum of two numbers. The `operationOnSum` function takes 3 arguments, the first number, the second number, and the operation that is to be performed on their sum (callback).
- Both `divideByHalf` and `multiplyBy2` functions are used as callback functions in the code above.
- These callback functions will be executed only after the function `operationOnSum` is executed.
- Therefore, a callback is a function that will be executed after another function gets executed.

### 2.3. Explain Scope and Scope Chain in javascript.

**Answer:**
Scope in JS determines the accessibility of variables and functions at various parts of one’s code.

In general terms, the scope will let us know at a given part of code, what are variables and functions we can or cannot access.

There are three types of scopes in JS:

- Global Scope
- Local or Function Scope
- Block Scope

**Global Scope**: Variables or functions declared in the global namespace have global scope, which means all the variables and functions having global scope can be accessed from anywhere inside the code.

```js
var globalVariable = "Hello world";

function sendMessage() {
  return globalVariable; // can access globalVariable since it's written in global space
}
function sendMessage2() {
  return sendMessage(); // Can access sendMessage function since it's written in global space
}
sendMessage2(); // Returns “Hello world”
```

**Function Scope**: Any variables or functions declared inside a function have `local/function scope`, which means that all the variables and functions declared inside a function, can be accessed from within the function and not outside of it.

```js
function awesomeFunction() {
  var a = 2;

  var multiplyBy2 = function () {
    console.log(a * 2); // Can access variable "a" since a and multiplyBy2 both are written inside the same function
  };
}
console.log(a); // Throws reference error since a is written in local scope and cannot be accessed outside

multiplyBy2(); // Throws reference error since multiplyBy2 is written in local scope
```

**Block Scope**: `Block scope` is related to the variables declared using let and const. Variables declared with var do not have block scope. Block scope tells us that any variable declared inside a block `{ }`, can be accessed only inside that block and cannot be accessed outside of it.

```js
{
  let x = 45;
}

console.log(x); // Gives reference error since x cannot be accessed outside of the block

for (let i = 0; i < 2; i++) {
  // do something
}

console.log(i); // Gives reference error since i cannot be accessed outside of the for loop block
```

**Scope Chain**: JavaScript engine also uses Scope to find variables. Let’s understand that using an example:

```js
var y = 24;

function favFunction() {
  var x = 667;
  var anotherFavFunction = function () {
    console.log(x); // Does not find x inside anotherFavFunction, so looks for variable inside favFunction, outputs 667
  };

  var yetAnotherFavFunction = function () {
    console.log(y); // Does not find y inside yetAnotherFavFunction, so looks for variable inside favFunction and does not find it, so looks for variable in global scope, finds it and outputs 24
  };

  anotherFavFunction();
  yetAnotherFavFunction();
}
favFunction();
```

As you can see in the code above, if the javascript engine does not find the variable in local scope, it tries to check for the variable in the outer scope. If the variable does not exist in the outer scope, it tries to find the variable in the global scope.

If the variable is not found in the global space as well, a reference error is thrown.

### 2.4. Explain Higher Order Functions in javascript.

**Answer:**
Functions that operate on other functions, either by taking them as arguments or by returning them, are called _higher-order functions_.

Higher-order functions are a result of functions being **first-class citizens** in javascript.

Examples of higher-order functions:

```js
function higherOrder(fn) {
  fn();
}

higherOrder(function () {
  console.log("Hello world");
});
function higherOrder2() {
  return function () {
    return "Do something";
  };
}
var x = higherOrder2();
x(); // Returns "Do something"
```

### 2.5. What do you mean by Self Invoking Functions in javascript?

**Answer:** Without being requested, a self-invoking expression is automatically invoked (initiated). If a function expression is followed by `()`, it will execute automatically. A function declaration cannot be invoked by itself.

Normally, we declare a function and call it, however, anonymous functions may be used to run a function automatically when it is described and will not be called again. And there is no name for these kinds of functions.


### 2.6. What is the difference between `exec()` and `test()` methods in javascript?

**Answer:** The following points discusses the differences between `test()` and `exec()` methods.

- `test()` and `exec()` are RegExp expression methods used in javascript.

- We'll use `exec()` to search a string for a specific pattern, and if it finds it, it'll return the pattern directly; else, it'll return an 'empty' result.
- We will use a `test()` to find a string for a specific pattern. It will return the Boolean value `true` on finding the given text otherwise, it will return `false`

### 2.7.  What is the difference between Function declaration and Function expression?

**Answer:** The difference between function declaration and function expression are as follows:

**Function declaration**:
<ol style="list-style-type: upper-alpha">
<li> Declared as a separate statement within the main JavaScript code.</li>
<li> Can be called before the function is defined.</li>
<li> Offers better code readability and better code organization.</li>

</ol>

Example:

```js
function abc() {
    return 5;
}
```


**Function expression**:
<ol style="list-style-type: upper-alpha">
<li>Created inside an expression or some other construct.</li>
<li>Created when the execution point reaches it; can be used only after that.</li>
<li>Used when there is a need for a conditional declaration of a function.</li>

</ol>

Example:

```js
var a = function abc() {
    return 5;
}
```


### 2.8. What are the arrow functions in JavaScript?

**Answer**: Arrow functions are a short and concise way of writing functions in JavaScript. The general syntax of an arrow function is as below:
```js
const helloWorld = () => {
  console.log("hello world!");
};
```

### 2.9. Passed by value and passed by reference :

**Answer:** 
- Passed By Values Are Primitive Data Types.  
Consider the following example:

Here, the `a=432` is a primitive data type i.e. a number type that has an assigned value by the operator.  When the `var b=a` code gets executed, the value of `var a` returns a new address for `var b` by allocating a new space in the memory, so that ‘var b’ will be operated at a new location. 

Example:
```js
var a = 432;
var b = a;
```


Passed_by_values_new

- Passed by References Are Non-primitive Data Types.

Consider the following example:

The reference of the 1st variable object i.e. `var obj` is passed through the location of another variable i.e. `var obj2` with the help of an assigned operator.

Example: 
```js
var obj = { name: "Raj", surname: "Sharma" };
var obj2 = obj;
```

# 3. Data Types and Operator

### 3.1. What are the different data types present in JavaScript?

**Answer:** The different data types present in JavaScript are as follows:

1. **Primitive types**

   - `String` - It represents a series of characters and is written with quotes. A string can be represented using a single or a double quote.

     **Example** :

     ```js
     var str = "Vivek Singh Bisht"; //using double quotes
     var str2 = "John Doe"; //using single quotes
     ```

   - `Number` - It represents a number and can be written with or without decimals.

     **Example** :

     ```js
     var x = 3; //without decimal
     var y = 3.6; //with decimal
     ```

   - `BigInt` - This data type is used to store numbers which are above the limitation of the Number data type. It can store large integers and is represented by adding “n” to an integer literal.

     **Example** :

     ```js
     var bigInteger = 234567890123456789012345678901234567890;
     ```

   - `Boolean` - It represents a logical entity and can have only two values : true or false. Booleans are generally used for conditional testing.

     **Example** :

     ```js
     var a = 2;
     var b = 3;
     var c = 2;
     (a == b)(
       // returns false
       a == c
     ); //returns true
     ```

   - `Undefined` - When a variable is declared but not assigned, it has the value of undefined and it’s type is also undefined.

     **Example** :

     ```js
     var x; // value of x is undefined
     var y = undefined; // we can also set the value of a variable as undefined
     ```

   - `Null` - It represents a non-existent or a invalid value.

     **Example** :

     ```js
     var z = null;
     ```

   - `Symbol` - It is a new data type introduced in the ES6 version of javascript. It is used to store an anonymous and unique value.

     **Example:**

     ```js
     var symbol1 = Symbol('symbol');
     typeof of primitive types :
     typeof "John Doe" // Returns "string"
     typeof 3.14 // Returns "number"
     typeof true // Returns "boolean"
     typeof 234567890123456789012345678901234567890n // Returns bigint
     typeof undefined // Returns "undefined"
     typeof null // Returns "object" (kind of a bug in JavaScript)
     typeof Symbol('symbol') // Returns Symbol 2. Non-primitive types
     ```

Primitive data types can store only a single value. To store multiple and complex values, non-primitive data types are used.

2. **Non-Primitive types**

   - `Object` - Used to store collection of data.

     **Example**:

     ```js
     // Collection of data in key-value pairs
     var obj1 = {
       x: 43,
       y: "Hello world!",
       z: function () {
         return this.x;
       },
     };
     ```

   - `Array`

     **Example:**

     ```js
     // Collection of data as an ordered list

     var array1 = [5, "Hello", true, 4.1];
     ```

> **Note- It is important to remember that any data type that is not a primitive data type, is of `Object` type in javascript.**

### 3.2 Difference between `==` and `===` operators.

**Answer:**
Both are comparison operators. The difference between both the operators is that `==` is used to compare values whereas, `===` is used to compare both values and types.

**Example**:

```js
var x = 2;
var y = "2";
(x == y)(
  // Returns true since the value of both x and y is the same
  x === y
); // Returns false since the typeof x is "number" and typeof y is "string"
```

### 3.3. What is NaN property in JavaScript?

**Answer:**
`NaN` property represents the “**Not-a-Number**” value. It indicates a value that is not a legal number.

`typeof` of `NaN` will return a Number.

To check if a value is `NaN`, we use the `isNaN()` function,

> Note- `isNaN()` function converts the given value to a Number type, and then equates to NaN.

**Example:**

```js
isNaN("Hello"); // Returns true
isNaN(345); // Returns false
isNaN("1"); // Returns false, since '1' is converted to Number type which results in 0 ( a number)
isNaN(true); // Returns false, since true converted to Number type results in 1 ( a number)
isNaN(false); // Returns false
isNaN(undefined); // Returns true
```

### 3.4. Which method is used to retrieve a character from a certain index?

**Answer:**
The `charAt()` function of the JavaScript string finds a char element at the supplied index. The index number begins at `0` and continues up to `n-1`, Here `n` is the string length. The index value must be positive, higher than, or the same as the string length.

# 4. Some important concepts

### 4.1. What is Hoisting in JavaScript?

**Answer:**
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Inevitably, this means that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local.

**Example 1:** Hoisting of variable
  
  ```js 
hoistedVariable = 3;
console.log(hoistedVariable); // outputs 3 even when the variable is declared after it is initialized	
var hoistedVariable;
```

**Example 2:** Hoisting of function
```js 
hoistedFunction();  // Outputs " Hello world! " even when the function is declared after calling

function hoistedFunction(){ 
  console.log(" Hello world! ");
} 
```
**Example 3:** Hoisting of function expression
```js 
// Hoisting takes place in the local scope as well
function doSomething(){
  x = 33;
  console.log(x);
  var x;
} 
doSomething(); // Outputs 33 since the local variable “x” is hoisted inside the local scope

/* Note - Variable initializations are not hoisted, only variable declarations are hoisted: */
var x;
console.log(x); // Outputs "undefined" since the initialization of "x" is not hoisted
x = 23;

/* Note - To avoid hoisting, you can run javascript in strict mode by using “use strict” on top of the code: */
"use strict";
x = 23; // Gives an error since 'x' is not declared
var x;
```
### 4.2. Why do we use the word “debugger” in javascript?

**Answer:** The `debugger` keyword is used to create breakpoints in the code. When the browser finds the debugger keyword in the code, it stops executing the code and opens the debugging tool of the browser.

### 4.3. What is currying in JavaScript?

**Answer:** Currying is an advanced technique to transform a function of arguments `n`, to `n` functions of one or fewer arguments.

*Example of a curried function:*
``` js
function add (a) {
  return function(b){
    return a + b;
  }
}

add(3)(4) 
```
For Example, if we have a function `f(a,b)`, then the function after currying, will be transformed to `f(a)(b)`.

By using the currying technique, we do not change the functionality of a function, we just change the way it is invoked.

Let’s see currying in action:

``` js
function multiply(a,b){
  return a*b;
}

function currying(fn){
  return function(a){
    return function(b){
      return fn(a,b);
    }
  }
}

var curriedMultiply = currying(multiply);

multiply(4, 3); // Returns 12

curriedMultiply(4)(3); // Also returns 12
```


As one can see in the code above, we have transformed the `function multiply(a,b)` to a function `curriedMultiply`, which takes in one parameter at a time.

### 4.4. What are some advantages of using External JavaScript?

**Answer:** External JavaScript is the JavaScript Code (script) written in a separate file with the `extension.js`, and then we link that file inside the `<head>` or `<body>` element of the HTML file where the code is to be placed. 

Some advantages of external javascript are:

- It allows web designers and developers to collaborate on HTML and javascript files.
- We can reuse the code.
- Code readability is simple in external javascript.

### 4.5. What is a closure in JavaScript?

**Answer:** A closure is a function that has access to its outer function scope even after the outer function has returned. This means a closure can remember and access variables and arguments of its outer function even after the function has finished.

In Short- A closure is a function that has access to variables from its outer (enclosing) function scope, even after the outer function has finished executing.

### 4.6. What is the DOM in JavaScript?

**Answer:** The Document Object Model (DOM) is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects. That way, programming languages can connect to the page.

### 4.7. What is event delegation?

**Answer:** Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it. The events are handled by the callback function of the parent element.

### 4.8. How can you make an AJAX request in JavaScript?

**Answer:** [AJAX](../miscellaneous/api-ajax.md) stands for Asynchronous JavaScript and XML. It is a set of web development techniques using many web technologies on the client-side to create asynchronous web applications. With AJAX, web applications can send and retrieve data from a server asynchronously (in the background) without interfering with the display and behavior of the existing page.

You can make AJAX requests using the XMLHttpRequest object or by using the fetch API. Here's an example using fetch:
  
```js
  fetch('https://example.com/api/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
```
### 4.9. What is a promise in JavaScript?

**Answer:** A promise is an object that may produce a single value sometime in the future: either a resolved value or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states:  `fulfilled`, `rejected`, or `pending`. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

### 4.10. Why do you need a promise in JavaScript ?

**Answer:** Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

### 4.11. Explain equality in JavaScript ?

**Answer:** JavaScript provides two types of equality operators: strict equality `(===)` and loose equality `(==)`

- Strict Equality `(===)`: This operator compares two values without performing any type conversion. If the values have different types, they are considered unequal. If the values have the same type, are not numbers, and have the same value, they are considered equal. For numbers, they are considered equal if they are both not NaN and have the same value, or if one is `+0` and the other is `-0`.

- Loose Equality `(==)`: This operator performs type conversion when comparing the operands. If the operands have the same type, they are compared in the same way as the strict equality operator. If the operands have different types, JavaScript attempts to convert them to a common type and then compare them. The rules for type conversion can sometimes lead to unexpected results, so it's generally recommended to use the strict equality operator to avoid potential issues


## 5. Object

### 5.1. What are the possible ways to create objects in JavaScript?

 
**Answer:** There are many ways to create objects in javascript as below

Object constructor:

i. The simplest way to create an empty object is using the Object constructor. Currently this approach is not recommended.
``` js
var object = new Object();
```
The Object() is a built-in constructor function so "new" keyword is not required. the above can be written as:
``` js
var object = Object();
```
ii. Object's create method:

The create method of Object creates a new object by passing the prototype object as a parameter

```js
var object = Object.create(null);
```
iii. Object literal syntax:


The object literal syntax (or object initializer), is a comma-separated set of name-value pairs wrapped in curly braces.

```js
var object = {
     name: "Sudheer",
     age: 34
};

Object literal property values can be of any data type, including array, function, and nested object.
```
Note: This is an easiest way to create an object

iv. Function constructor:

Create any function and apply the new operator to create object instances,

```js
function Person(name) {
  this.name = name;
  this.age = 21;
}
var object = new Person("Sudheer");
```
v. Function constructor with prototype:

This is similar to function constructor but it uses prototype for their properties and methods,
```js
function Person() {}
Person.prototype.name = "Sudheer";
var object = new Person();
```
This is equivalent to an instance created with an object create method with a function prototype and then call that function with an instance and parameters as arguments.
```js
function func() {}

new func(x, y, z);
```
(OR)
```js
// Create a new instance using function prototype.
var newInstance = Object.create(func.prototype)

// Call the function
var result = func.call(newInstance, x, y, z),

// If the result is a non-null object then use it otherwise just use the new instance.
console.log(result && typeof result === 'object' ? result : newInstance);
```
vi. ES6 Class syntax:

ES6 introduces class feature to create the objects
```js
class Person {
  constructor(name) {
    this.name = name;
  }
}

var object = new Person("Sudheer");
```


## 6.Miscellaneous

### 6.1. What is a strict mode in JavaScript ?

**Answer:** Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a "strict" operating context. This way it prevents certain actions from being taken and throws more exceptions. The literal expression "use strict"; instructs the browser to use the javascript code in the Strict mode.

### 6.2. What is null value in JavaScript ?

**Answer:** The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values. The type of null value is object. You can empty the variable by setting the value to null.

```js
var user = null;
console.log(typeof user); //object
```

### 6.3. What is `eval` in JavaScript ?

**Answer:** The `eval()` function evaluates JavaScript code represented as a string. The string can be a JavaScript expression, variable, statement, or sequence of statements.

```js
console.log(eval("1 + 2")); //  3
```

### 6.4. Is JavaScript a compiled or interpreted language ?

**Answer:** JavaScript is an interpreted language, not a compiled language. An interpreter in the browser reads over the JavaScript code, interprets each line, and runs it. Nowadays modern browsers use a technology known as Just-In-Time (JIT) compilation, which compiles JavaScript to executable bytecode just as it is about to run.

### 6.5. difference between `exec()` and `test()` methods

**Answer** The differences between `exec()` and `test()` methods are as follows:

`exec()`:
1) It is an expression method in JavaScript that is used to search a string with a specific pattern. 
2) Once it has been found, the pattern will be returned directly, otherwise, it returns an “empty” result.

`test()`:
1) It is an expression method in JavaScript that is also used to search a string with a specific pattern or text. 
2) Once it has been found, the pattern will return the Boolean value `true`, else it returns `false`. 

### 6.6. Is JavaScript a case-sensitive language ?

**Answer:** Yes, JavaScript is a case sensitive language. The language keywords, variables, function & object names, and any other identifiers must always be typed with a consistent capitalization of letters.

## 7.JSON

### 7.1. What is JSON ?

**Answer:** JSON (JavaScript Object Notation) is a lightweight format that is used for data interchanging. It is based on a subset of JavaScript language in the way objects are built in JavaScript.

### 7.2. What are the syntax rules of JSON ?

**Answer:**  Below are the list of syntax rules of JSON

*  The data is in name/value pairs
*  The data is separated by commas
*  Curly braces hold objects
*  Square brackets hold arrays

### 7.3. What is the purpose JSON stringify ?

**Answer:** When sending data to a web server, the data has to be in a string format. You can achieve this by converting JSON object into a string using `stringify()` method.

```js
var userJSON = { name: "John", age: 31 };
var userString = JSON.stringify(userJSON);
console.log(userString); //"{"name":"John","age":31}"
```

### 7.4. How do you parse JSON string ?

**Answer:** When receiving the data from a web server, the data is always in a string format. But you can convert this string value to a javascript object using `parse()` method.

```js
var userString = '{"name":"John","age":31}';
var userJSON = JSON.parse(userString);
console.log(userJSON); // {name: "John", age: 31}
```

### 7.5. Why do you need JSON ?

**Answer:** When exchanging data between a browser and a server, the data can only be text. Since JSON is text only, it can easily be sent to and from a server, and used as a data format by any programming language.

### 7.6. How do you define JSON arrays ?

**Answer:**  JSON arrays are written inside square brackets and arrays contain javascript objects. For example, the JSON array of users would be as below,

```js
"users":[
  {"firstName":"John", "lastName":"Abrahm"},
  {"firstName":"Anna", "lastName":"Smith"},
  {"firstName":"Shane", "lastName":"Warn"}
]
```

### 7.6. In JSON, what is the purpose of square brackets, and how are they used?

**Answer:** In JSON, square brackets `[ ]` are used to encapsulate and define arrays within JSON data structures. JSON arrays can contain a collection of values, which can be of various data types, including objects, strings, numbers, and other JSON arrays.

# Intermediate Level JavaScript Interview Questions
## 1. Loops
### 1.1. What is the definition of an iteration in a JavaScript loop?

**Answer:** An iteration in a JavaScript loop refers to each individual execution of the loop's body, typically corresponding to one cycle of the loop.

### 1.2. What are all the looping structures in JavaScript?

**Answer:** Various looping structures are used in JavaScript. Some of them are as follows:

**While loop**: A [while](../loops/while.md) loop is a control flow statement that allows code to be executed repeatedly based on a given Boolean condition. The while loop can be thought of as a repeating if statement.

**For loop**: A [for](../loops/for.md) loop provides a concise way of writing the loop structure. Unlike a while loop, for statement consumes the initialization, condition and increment/decrement in one line thereby providing a shorter, easy to debug structure of looping.

**Do while**: A [do-while](../loops/dowhile.md) loop is similar to while loop with the only difference that it checks the condition after executing the statements, and therefore is an example of Exit Control Loop.

### 1.3. How does the break statement work in a loop?

**Answer:** The break statement terminates the current loop or switch statement and transfers program control to the statement following the terminated statement. It can also be used to jump past a labeled statement when used within that labeled statement.

### 1.4. How does the continue statement work in a loop?

**Answer:** The continue directive is a "lighter version" of the break statement. It does not stop the whole loop; instead, it stops the current iteration and forces the loop to start a new one (if the condition allows).

## 2. Switch statement

### 2.1. What is a switch statement in JavaScript?

**Answer:** A switch statement in JavaScript is a control flow statement that evaluates an expression and executes a specific block of code based on the matched case.

### 2.2. What are the advantages of employing a Switch statement?

**Answer:** A [switch](../conditional/switch.md) statement can replace multiple checks, and it is more descriptive and easier to read. Switch statements improve code readability, provide better performance, simplify complex conditionals, enhance maintainability, and support cleaner syntax.

### 2.3. Is the order of case statements important in a switch statement?

**Answer:** The order of case statements is important in a switch statement, especially when employing fall-through behavior. Cases are evaluated sequentially, so a matching case found earlier will prevent subsequent cases from being tested, affecting execution and performance.

## 3. JavaScript cookies

### 3.1. What are JavaScript Cookies ?

**Answer:** [Cookies](../browser-object-model-bom/cookies.md) are small files that are stored on a user’s computer. They are used to hold a modest amount of data specific to a particular client and website and can be accessed either by the web server or by the client’s computer. When cookies were invented, they were basically little documents containing information about you and your preferences. For instance, when you select the language in which you want to view your website, the website would save the information in a document called a cookie on your computer, and the next time when you visit the website, it would be able to read a cookie saved earlier.

### 3.2.  How to create a cookie using JavaScript?

**Answer:** To create a cookie by using JavaScript you just need to assign a string value to the document.cookie object.
````javascript
document.cookie = "key1 = value1; key2 = value2; expires = date";
````

### 3.3. How to read a cookie using JavaScript?

**Answer:** The value of the document.cookie is used to create a cookie. Whenever you want to access the cookie you can use the string. The `document.cookie` string keep a list of `name = value` pairs separated by semicolons, where name is the name of a cookie and the value is its string value.

### 3.4. How to delete a cookie using JavaScript?

**Answer:** Deleting a cookie is much easier than creating or reading a cookie, you just need to set the expires = “past time” and make sure one thing defines the right cookie path unless few will not allow you to delete the cookie.

## 4. Pop-up boxes in JavaScript
 
### 4.1. What are the types of Pop up boxes available in JavaScript?

**Answer:** There are three types of pop boxes available in JavaScript:
`Alert`, `Confirm`, `Prompt`.

### 4.2. What is the difference between an alert box and a confirmation box?

**Answer:** An alert box will display only one button which is the OK button. It is used to inform the user about the agreement has to agree. But a Confirmation box displays two buttons OK and cancel, where the user can decide to agree or not.

## 5. Arrow Functions

### 5.1. What is the definition of an arrow function?

**Answer:** An arrow function is a concise syntax for defining anonymous functions in JavaScript, using the arrow notation. It offers shorter syntax, lexical scoping of "this", and can't be used as a constructor.

### 5.2. How do arrow functions differ from function expressions?

**Answer:** Arrow functions provide a shorter syntax, don't have their own this, arguments, super, or new.target, and can't be used as constructors, unlike function expressions.

### 5.3. What does lexical 'this' binding mean in arrow functions?

**Answer:** "Lexical this" binding in arrow functions means they don't create their own 'this' context; instead, they inherit 'this' from their surrounding, enclosing scope, reducing common 'this'-related issues.

### 5.4. What are the advantages of using arrow functions?

**Answer:** The advantages of using arrow functions in JavaScript include shorter syntax, implicit return, and lexical ‘this’ binding.

### 5.5. What are the common use cases for arrow functions?

**Answer:** Arrow functions are commonly used for object methods, event listeners, callbacks, and other functions that require shorter, more concise syntax.


## 6. Regular Expression

### 6.1. What is a Regular Expression ?

**Answer:** A regular expression is a sequence of characters that forms a search pattern. You can use this search pattern for searching data in a text. These can be used to perform all types of text search and textreplace operations. Let's see the syntax format now,
   
```js
 /pattern/modifiers;
```

For example, the regular expression or search pattern with case-insensitive username would be,

```js
/John/i;
```

### 6.2. What are the string methods available in Regular expression ?

**Answer:** Regular Expressions has two string methods: search() and replace(). The search() method uses an expression to search for a match, and returns the position of the match.

```js
var msg = "Hello John";
var n = msg.search(/John/i); // 6
```

The replace() method is used to return a modified string where the pattern is replaced.

```js
var msg = "Hello John";
var n = msg.replace(/John/i, "Buttler"); // Hello Buttler
```

### 6.3. What are modifiers in regular expression ?

**Answer:** Modifiers can be used to perform case-insensitive and global searches. Let's list down some of the modifiers:

| Modifier | Description                                      |
| -------- | ------------------------------------------------ |
| `i`      | Perform case-insensitive matching.               |
| `g`      | Perform a global match (find all matches).       |
| `m`      | Perform multiline matching.                      |

Let's take an example of global modifier,

```js
var text = "Learn JS one by one";
var pattern = /one/g;
var result = text.match(pattern); // one,one
```

### 6.4. What are regular expression patterns ?

**Answer:** Regular Expressions provide a group of patterns in order to match characters. Basically they are categorized into 3 types,
  
  + i.Brackets: These are used to find a range of characters. For example, below are some use cases,
    - a. [abc]: Used to find any of the characters between the brackets(a,b,c).
    - b. [0-9]: Used to find any of the digits between the brackets.
    - c. (a|b): Used to find any of the alternatives separated with |
  + ii.Metacharacters: These are characters with a special meaning For example, below are some use cases 
    - a. \d: Used to find a digit 
    - b. \s: Used to find a whitespace character
    - c. \b: Used to find a match at the beginning or ending of a word
  + iii.Quantifiers: These are useful to define quantities For example, below are some use cases
    - a. n+: Used to find matches for any string that contains at least one n 
    - b. n*: Used to find matches for any string that contains zero or more occurrences of n 
    - c. n?: Used to find matches for any string that contains zero or one occurrences of n

### 6.5. What is a RegExp object ?

**Answer:** RegExp object is a regular expression object with predefined properties and methods. Let's see the simple usage of RegExp object,

```js
var regexp = new RegExp("\\w+");
console.log(regexp);
// expected output: /\w+/
```

### 6.6. How do you search a string for a pattern ?

**Answer:**  You can use the `test()` method of regular expression in order to search a string for a pattern, and return true or false depending on the result.

```js
var pattern = /you/;
console.log(pattern.test("How are you?")); //true
```
### 6.7. What is Currying in Javascript?
 
**Answer:** Currying in JavaScript transforms a function with multiple arguments into a nested series of functions, each taking a single argument. Currying helps you avoid passing the same variable multiple times, and it helps you create a higher order function.

That is, when we turn a function call `sum(1,2,3)` into `sum(1)(2)(3)`. 

The number of arguments a function takes is also called arity.

```js
function sum(a, b) {
    // do something
}
function _sum(a, b, c) {
    // do something
}
```
The function sum takes two arguments (two-arity function) and _sum takes three arguments (three-arity function).

Curried functions are constructed by chaining closures and by defining and immediately returning their inner functions simultaneously.

## 7. Temporal Dead Zone

### 7.1. What is the Temporal Dead Zone in ES6?
 
**Answer:** In ES6 let and const are hoisted (like var , class and function ), but there is a period between entering scope 
and being declared where they cannot be accessed. This period is the temporal dead zone (TDZ)

```javascript
//console.log(aLet)  // would throw ReferenceError 
let aLet; 
console.log(aLet); // undefined 
aLet = 10; 
console.log(aLet); // 10
```


### 7.2. What are Truthy and Falsy Values in JavaScript?
 
**Answer:** In JavaScript, "truthy" and "falsy" are terms used to describe how values are evaluated in Boolean contexts, such as conditions in if statements and loops. Understanding truthy and falsy values is crucial when working with conditional logic.

#### Falsy Values:

- `false`: The Boolean value false.
- `0`: The numeric value zero.
- `""`: An empty string.
- `null`: A special value indicating the absence of an object.
- `undefined`: A variable that has not been assigned a value.
- `NaN`: Stands for "Not-a-Number" and represents an invalid number.
- When any of these values are used in a Boolean context, they are treated as "falsy," meaning they are considered equivalent to false.

Examples of falsy values:
```javascript
if (false) {
    // This code block won't execute because false is falsy.
}

if (0) {
    // This code block won't execute because 0 is falsy.
}

if ("" === false) {
    // This comparison is true because an empty string is falsy.
}

if (null) {
    // This code block won't execute because null is falsy.
}

if (undefined) {
    // This code block won't execute because undefined is falsy.
}

if (NaN) {
    // This code block won't execute because NaN is falsy.
}
```
#### Truthy Values:

Any value that is not explicitly "falsy" is considered "truthy" in JavaScript. These values are treated as equivalent to true in Boolean contexts.

Example of truth values:
```javascript
if (true) {
    // This code block will execute because true is truthy.
}

if (42) {
    // This code block will execute because 42 is truthy.
}

if ("Hello") {
    // This code block will execute because a non-empty string is truthy.
}

if ({} === true) {
    // This comparison is false because an empty object is truthy but not equal to true.
}

if ([] === true) {
    // This comparison is false because an empty array is truthy but not equal to true.
}
```

Understanding truthy and falsy values allows us to write more concise and expressive code, especially when dealing with conditional logic. We can use this behavior to write shorter and more readable code when evaluating conditions and choosing between two values or actions.

## 8. Classes

### 8.1. What are JavaScript classes?

**Answer:** Classes are templates for creating objects. They encapsulate data and logic that works with the data.

### 8.2. What are class members?

**Answer:** Class members refer to the methods and fields within a class.

  + i. Methods
    - Functions that are defined within the class.
    - They can operate on fields and perform actions with the data.
    - They define the behavior of the class.
  + ii. Fields
    - Variables that are defined within the class.
    - They hold data specific to the class instance.
    - They define the state of the class.

### 8.3. Explain the types of access modifiers and their purpose in JavaScript

**Answer:** There are three types of access modifiers which are used to encapsulate information.

  + Public
    - Can be accessed from anywhere.
  + Private
    - Indicated by prefixing members with the ```#``` symbol.
    - Cannot be accessed from instances or child classes.
    - Only available within the class itself.
    - Useful for information hiding.
  + Protected
    - Indicated by prefixing members with the ```_``` symbol.
    - Can be accessed from the within the class and any class that inherits from it.
    - Useful for sharing state between classes.


### 8.4. What are class properties?
**Answer:** Properties refer to the getter and setter within a class, which provide a way to control access to the fields of a class. The getter and setter are property bindings to a function that will be called when the property is accessed.

  + i. Getter
    - A getter is a method that gets the value of a field.
    - It must have exactly zero parameters.
    - It must return a value.
    - It is defined using the ```get``` keyword.
  + ii. Setter
    - A setter is a method that sets the value of a field.
    - It must have exactly one parameter.
    - It is defined using the ```set``` keyword.

They are used to encapsulate the data, ensuring only certain fields can be accessed or modified in a specific way.

Example of encapsulation using getters and setters:

```javascript
  class Task {
    #id;
    #description;

    constructor(id, description, ) {
      //  Use setters instead of directly modifying the private fields
      this.id = id;
      this.description = description;
    }

    //  Use getters to read the values
    get id() {
      return this.#id;
    }

    //  ...

    //  Use setters to validate data before writing
    set id(id) {
      //  ...validate new ID
      this.#id = id;
    }

    //  ...
  }
```

### 8.5. Explain class constructors

**Answer:** The constructor is a special method of a class called upon the initialization of that class. It is used to initialize the object's properties and perform any setup that is necessary when the object is created.

  + i. Declaration
    - The constructor method is declared using the ```constructor``` keyword within the class body.
    - Each class can only have one constructor method.
    - The constructor cannot be an async method.
    - The constructor cannot be a private method.
  + ii. Initialization
    - The constructor can accept parameters that are used to initialize the instance's properties.
    - It sets up the initial state by assigning values to properties.
  + iii. Inheritance
    - In derived classes (classes that extend another class), the ```super``` keyword is used within the child's constructor to call the constructor of the parent class.
    - The ```super``` call must be made before accessing any properties in the constructor of a derived class. Example of constructor inheritance:

    ```javascript
    class Animal {
        constructor(species) {
            this.species = species;
        }
    }

    class Person extends Animal {
        constructor(name) {
            super("Human"); //  Call the parent class constructor
            this.name = name;
        } 
    }
    ```
  + iv. Default constructor - If no constructor is explicitly declared, a default one will be given to the class.
    - Base class - If the class doesn't extend any other class, a default constructor will be assigned to it:
    ```javascript
      constructor() {}
    ```
    - Child class - If the class extends another class, it will inherit its constructor
    ```javascript
      class Vehicle {
        constructor(type) {
          this.type = type;
        }

        move() {
          return `The ${this.type} is moving`;
        }
      }

      class Car extends Vehicle {
        #model;

        set model(model) {
          this.#model = model;
        }
        
        drive() {
          `Driving ${this.#model}`;
        }
      }
    ```
    Even though the constructor is not explicitly declared, the class Car inherits it from the Vehicle class:
    ```javascript
      constructor(type) {
        super(type);
      }
    ``` 

### 8.6. Static members vs Instance members

**Answer:** By default, properties and methods which we define inside a class belong to each instance of the class that we create. We can also assign members to the class itself. Such members are called static and are declared using the ```static``` keyword. They cannot be directly accessed on instances of the class.

# Advanced JavaScript Interview Questions

## 1. Closures and Scoping

### 1.1. What is a closure in JavaScript? Provide an example where using closures can be beneficial.

**Answer:** A closure in JavaScript is a function that has access to its enclosing scope's variables, even after the outer function has finished executing. This mechanism allows functions to maintain state between executions.

**Example:**
One common use of closures is to create factory functions or private variables. For instance, if we wanted to generate unique ID values for elements:
```javascript
function createUniqueIdGenerator() {
  let id = 0;
  return function() {
    return id++;
  };
}

const generateId = createUniqueIdGenerator();

console.log(generateId()); // 0
console.log(generateId()); // 1
console.log(generateId()); // 2
```
### 1.2. How do closures relate to variables' scope and lifetime?

**Answer:** Closures allow a function to access all the variables, as well as functions, that are in its lexical scope, even after the outer function has completed. This results in the variables being preserved in memory, effectively allowing for variables to have a prolonged lifetime compared to standard local variables which would typically be garbage collected after their parent function has executed.

### 1.3. Give some examples of uses of closures in javascript?

**Answer:** Here are some example of closures.
- Module Design Pattern.
- Currying.
- Memoize

## 2. Prototypal Inheritance

### 2.1. Explain the difference between classical inheritance and prototypal inheritance.

**Answer:** Classical inheritance is a concept most often found in traditional Object-Oriented Programming languages like Java or C++, where a class can inherit properties and methods from a parent class. Prototypal inheritance, on the other hand, is unique to JavaScript. In JavaScript, each object can have another object as its prototype, and it can inherit properties from its prototype.

The primary difference is that classical inheritance is class-based, whereas prototypal inheritance is object-based. Although ES6 introduced the `class` keyword to JavaScript, it's syntactical sugar over the existing prototypal inheritance.

### 2.2. How can you extend built-in JavaScript objects?

**Answer:** To extend built-in JavaScript objects, we can add methods or properties to their prototype. However, it's generally discouraged to modify native prototypes because it can lead to compatibility issues and unexpected behavior, especially if there are future changes to the JavaScript specification.

## 3. Asynchronous JavaScript

### 3.1. Explain the event loop in JavaScript. How does it relate to the call stack?

**Answer:** The event loop is a fundamental concept in JavaScript and is responsible for handling the execution of multiple chunks of program over time, each run to completion. It works as a continuous loop that checks if there are tasks waiting in the message queue. If there are tasks and the main thread (call stack) is empty, it dequeues the task and executes it.

The call stack, on the other hand, is a data structure that tracks the execution of functions in a program. When a function is called, it is added to the call stack, and when it finishes executing, it is removed from the stack.

In the context of JavaScript, the event loop continuously checks the call stack to determine if it is empty. If it is empty and there are callback functions waiting in the message queue, those callbacks are executed.

### 3.2. What are promises, and how do they differ from callbacks in managing asynchronous operations?

**Answer:** Promises are objects representing the eventual completion (or failure) of an asynchronous operation and its resulting value. A `Promise` is in one of these states:

- `pending`: initial state, neither fulfilled nor rejected.
- `fulfilled`: meaning the promised operation has completed and the promise has a resulting value.
- `rejected`: meaning the operation failed, and the promise will never be fulfilled.

Callbacks are functions that are passed into another function as arguments and are executed after the outer function has completed. While both promises and callbacks can handle asynchronous operations, promises provide a more robust way of handling them.

The key differences include:

- Promises allow for better chaining of asynchronous operations.
- Callbacks can lead to callback hell or pyramid of doom, where the code becomes hard to read and manage due to nested callbacks.
- Promises have a standardized error handling mechanism using `.then` and `.catch`.

### 3.3. Describe async/await. How does it simplify working with asynchronous code?

**Answer:** `async/await` is a syntactic feature introduced in ES8 (or ES2017) to work with asynchronous code in a more synchronous-like fashion. It allows for writing asynchronous operations in a linear manner without callbacks, leading to cleaner, more readable code.

The `async` keyword is used to declare an asynchronous function, which ensures that the function returns a promise. The `await` keyword is used inside an `async` function to pause the execution until the promise is resolved or rejected.

Using `async/await` simplifies error handling, as we can use traditional try/catch blocks instead of `.catch` with promises.

## 4. Advanced Array Methods

### 4.1. Describe the functions of `map`, `reduce`, and `filter`. Provide an example of a practical use case for each.

**Answer:** `map`, `reduce`, and `filter` functions are defined below.

- `map`: It transforms each element of an array based on a function, returning a new array of the same length.
  **Example:** Doubling each number in an array.
  ```javascript
  const numbers = [1, 2, 3, 4];
  const doubled = numbers.map((num) => num * 2); // [2, 4, 6, 8] ```
  ```
- `reduce`: It applies a function against an accumulator and each element in the array (from left to right), reducing it to a single value..
  **Example:** Summing all numbers in an array.
  ```javascript
  const numbers = [1, 2, 3, 4];
  const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0); // 10
  ```
- `filter`: It creates a new array with elements that pass a test specified by a function.
**Example:** Summing all numbers in an array.
  ```javascript
  const numbers = [1, 2, 3, 4, 5, 6];
  const evenNumbers = numbers.filter((num) => num % 2 === 0); // [2, 4, 6]
  ```

### 4.2. What are some limitations or pitfalls when using arrow functions?

**Answer:** Arrow functions introduce a concise way to write functions in JavaScript, but they come with certain limitations:

1. **No `this` Binding**: Arrow functions do not bind their own `this`. They inherit the `this` binding of the surrounding scope. This can be problematic, especially when using them as methods in objects or as event handlers.

2. **No `arguments` Object**: Arrow functions do not have the `arguments` object of their own. If we need to access the arguments object, we'd have to use traditional function expressions.

3. **Cannot be Used as Constructors**: Arrow functions cannot be used as constructors with the `new` keyword because they don't have the `[[Construct]]` internal method.

4. **No `prototype` Property**: Unlike regular functions, arrow functions do not have a `prototype` property.

5. **Less Readable for Complex Logic**: For simple operations, the concise syntax is beneficial. However, for functions containing complex logic, the concise syntax might make the code less readable.

## 5. "this" Keyword

### 5.1. Explain the behavior of the `this` keyword in different contexts, such as in a method, a standalone function, an arrow function, and an event handler.
**Answer:** The `this` word can vary on depending upon the context it's used. Some of them are explored below:

- In Method: It refers to the object that the method is called on.

```js
const person = {
  name: "Alice",
  sayHello: function () {
    console.log(`Hello, my name is ${this.name}`);
  },
};

person.sayHello(); // Output: Hello, my name is Alice
```
- In Standalone Function:  Here, the `this` behavior depends on how function is called. If the function is called in the global scope, `this` refer to the global object.

```js
function greet() {
  console.log(`Hello, my name is ${this.name}`);
}

const name = "Alice";
greet(); // Output: Hello, my name is Alice
```
- In Arrow Function: Arrow functions capture the this value from their surrounding lexical scope, unlike regular functions. This means they lack their own this context.

```js
const person = {
  name: "Bob",
  sayHello: () => {
    console.log(`Hello, my name is ${this.name}`);
  },
};

person.sayHello(); // Output: Hello, my name is undefined
```

### 5.2. How can you ensure a function uses a specific object as its `this` value?
**Answer:**
We can ensure a function uses a specific object as its this value in JavaScript using methods like bind, arrow functions, call, apply, or by defining methods within ES6 classes. These techniques allow us to control the context in which the function operates and ensure it accesses the desired object's properties and methods.

## 6. Memory Management

### 6.1. What are memory leaks in JavaScript? Discuss potential causes and how to prevent them.
**Answer:**
Memory leaks in JavaScript occur when the program unintentionally retains references to objects that are no longer needed, leading to increased memory usage and potential application issues. Common causes include unused variables, closures, event listeners, and circular references. To prevent memory leaks, developers should explicitly remove references, manage event listeners, avoid circular dependencies, use weak references, employ memory profiling tools, conduct testing and code reviews, and utilize linters and static analysis tools to detect potential issues early in the development process.

### 6.2. Describe the difference between shallow copy and deep copy. How can you achieve each in JavaScript?
**Answer:**
Shallow copy and deep copy are methods for duplicating objects or arrays in JavaScript.

Shallow copy duplicates the top-level structure and values of an object or array but retains references to nested objects or arrays. Changes to nested structures affect both the original and the copy.
Deep copy creates a new object or array and recursively duplicates all levels of nested structures, ensuring changes in the copy do not affect the original.
To achieve a shallow copy, we can use methods like the spread operator or slice(). For a deep copy, custom logic or libraries like lodash's cloneDeep are necessary due to the lack of built-in deep copy methods in JavaScript.

## 7. ES6 and Beyond

### 7.1. Explain the purpose and usage of JavaScript's destructuring assignment.
**Answer:**
JavaScript's destructuring assignment is a feature that simplifies the extraction of values from objects and arrays, making code more concise and readable. It allows us to assign values to variables based on property names (object destructuring) or position (array destructuring). Destructuring can also be used in function parameters and supports the rest syntax to capture remaining elements. It's a powerful tool for working with complex data structures.

### 7.2. Describe the significance of JavaScript modules and the ES6 `import/export` syntax.
**Answer:**
JavaScript modules, along with the ES6 import/export syntax, are crucial for modern JavaScript development. They enable developers to organize, reuse, and maintain code effectively. Modules encapsulate related code, promote code reusability, manage dependencies, and improve code scalability. The ES6 import/export syntax provides a standardized way to declare and use modules, making it easier to structure and share code in a clean and maintainable manner. These features have become essential for building modular and maintainable JavaScript applications, both on the client and server sides.
### 7.3. How do template literals enhance string manipulation in ES6? Provide examples.
**Answer:**
Template literals in ES6 enhance string manipulation by allowing developers to create strings with embedded expressions and multiline content in a more readable and flexible way. They support variable interpolation, multiline strings, expression evaluation, function calls, and even advanced use cases like tagged templates. This feature improves code readability and maintainability when working with complex strings that involve dynamic content or expressions.

### 7.4. Can I redeclare let and const variables ?

**Answer:** No, you cannot redeclare let and const variables. If you do, it throws below error.

```js
Uncaught SyntaxError: Identifier 'someVariable' has already been declared
```

Explanation: The variable declaration with var keyword refers to a function scope and the variable is treated as if it were declared at the top of the enclosing scope due to hoisting feature. So all the multiple declarations contributing to the same hoisted variable without any error. Let's take an example of re-declaring variables in the same scope for both var and let/const variables.

```js
var name = "John";
function myFunc() {
  var name = "Nick";
  var name = "Abraham"; // Re-assigned in the same function block
  alert(name); // Abraham
}
myFunc();
alert(name); // John
```

The block-scoped multi-declaration throws syntax error,

```js
let name = "John";
function myFunc() {
  let name = "Nick";
  let name = "Abraham"; // Uncaught SyntaxError: Identifier 'name' has already been declared
  alert(name);
}

myFunc();
alert(name);
```

### 7.5. Is const variable makes the value immutable ?

**Answer:** No, the const variable doesn't make the value immutable. But it disallows subsequent assignments(i.e, You can declare with assignment but can't assign another value later)

```js
const userList = [];
userList.push("John"); // Can mutate even though it can't re-assign
console.log(userList); // ['John']
```

### 7.6. What are default parameters ?

**Answer:** In ES5, we need to depend on logical OR operators to handle default values of function parameters. Whereas in ES6, Default function parameters feature allows parameters to be initialized with default values if no value or undefined is passed. Let's compare the behavior with an examples,

```js
//ES5
var calculateArea = function (height, width) {
  height = height || 50;
  width = width || 60;

  return width * height;
};
console.log(calculateArea()); //300
```

The default parameters makes the initialization more simpler,

```js
//ES6
var calculateArea = function (height = 50, width = 60) {
  return width * height;
};

console.log(calculateArea()); //300
```

### 7.7. What are template literals ?

**Answer:** Template literals or template strings are string literals allowing embedded expressions. These are enclosed by the back-tick *(`)* character instead of double or single quotes. In ES6, this feature enables using dynamic expressions as below,

```js
var greeting = `Welcome to JS World, Mr. ${firstName} ${lastName}.`;
```

In ES5, you need break string like below,

```js
var greeting = 'Welcome to JS World, Mr. ' + firstName + ' ' + lastName.`
```

Note: You can use multi-line strings and string interpolation features with template literals.

### 7.8. How do you write multi-line strings in template literals ?

**Answer:** In ES5, you would have to use newline escape characters `('\n')` and concatenation symbols `(+)` in order to get multi-line strings.

```js
console.log("This is string sentence 1\n" + "This is string sentence 2");
```

Whereas in ES6, You don't need to mention any newline sequence character,

```js
console.log(`This is string sentence 'This is string sentence 2`);
```

### 7.9. What are nesting templates ?

**Answer:** The nesting template is a feature supported within template literals syntax to allow inner backticks inside a placeholder `${ }` within the template. For example, the below nesting template is used to display the icons based on user permissions whereas outer template checks for platform type:

```js
const iconStyles = `icon ${
  isMobilePlatform()
    ? ""
    : `icon-${user.isAuthorized ? "submit" : "disabled"}`
}`;
```
You can write the above use case without nesting template features as well. However, the nesting template feature is more compact and readable.

```js
//Without nesting templates
const iconStyles = `icon ${
  isMobilePlatform()
    ? ""
    : user.isAuthorized
    ? "icon-submit"
    : "icon-disabled"
}`;
```

### 7.10. What are tagged templates ?

**Answer:** Tagged templates are the advanced form of templates in which tags allow you to parse template literals with a function. The tag function accepts the first parameter as an array of strings and remaining parameters as expressions. This function can also return manipulated strings based on parameters. Let's see the usage of this tagged template behavior of an IT professional skill set in an organization,

```js
var user1 = "John";
var skill1 = "JavaScript";
var experience1 = 15;

var user2 = "Kane";
var skill2 = "JavaScript";
var experience2 = 5;

function myInfoTag(strings, userExp, experienceExp, skillExp) {
  var str0 = strings[0]; // "Mr/Ms. "
  var str1 = strings[1]; // " is a/an "
  var str2 = strings[2]; // "in"

  var expertiseStr;
  if (experienceExp > 10) {
    expertiseStr = "expert developer";
  } else if (skillExp > 5 && skillExp <= 10) {
    expertiseStr = "senior developer";
  } else {
    expertiseStr = "junior developer";
  }

  return `${str0}${userExp}${str1}${expertiseStr}${str2}${skillExp}`;
}

var output1 = myInfoTag`Mr/Ms. ${user1} is a/an ${experience1} in ${skill1}`;
var output2 = myInfoTag`Mr/Ms. ${user2} is a/an ${experience2} in ${skill2}`;

console.log(output1); // Mr/Ms. John is a/an expert developer in JavaScript
console.log(output2); // Mr/Ms. Kane is a/an junior developer in JavaScript
```

### 7.11. What are raw strings ?

**Answer:** ES6 provides a raw strings feature using the `String.raw()` method which is used to get the raw string form of template strings. This feature allows you to access the raw strings as they were entered, without processing escape sequences. For example, the usage would be as below,

```js
 var calculationString = String.raw`The sum of numbers is \n${
  1 + 2 + 3 + 4
}!`;
console.log(calculationString); // The sum of numbers is \n10!
```

If you don't use raw strings, the newline character sequence will be processed by displaying the output in multiple lines

```js
var calculationString = `The sum of numbers is \n${1 + 2 + 3 + 4}!`;
console.log(calculationString);
// The sum of numbers is
// 10!
```

Also, the raw property is available on the first argument to the tag function

```js
function tag(strings) {
  console.log(strings.raw[0]);
}
```

## 8. Functional Programming

### 8.1. How does functional programming differ from imperative programming in JavaScript?

**Answer:** Functional programming and imperative programming are two predominant programming paradigms.

- **Imperative Programming**: This paradigm is about telling the computer "how" to do something and relies on statements that change a programs state. In essence, it focuses on describing the steps to achieve a particular task. This often involves loops, conditionals, and statements that modify variables.

  ````javascript
  let total = 0;
  for(let i = 0; i < array.length; i++) {
      total += array[i];
  }```
  ````

#### Functional Programming (FP)

FP is more about instructing the computer "what" to achieve, rather than detailing "how" to achieve it. It treats computational tasks as evaluations of mathematical functions and steers clear of mutable data and state alterations. In the context of JavaScript and most FP languages:

- **Pure Functions**: These are functions where the output value is determined solely by its input values, without observable side effects. This means, for the same input, the function will always produce the same output.

- **Immutable Data**: Once data is created, it can never change. Instead of altering existing data, functional programming practices involve creating new data structures.

- **First-Class and Higher-Order Functions**: In FP, functions are first-class citizens. This means they can be assigned to variables, passed into other functions as parameters, and returned as values. A higher-order function is a function that receives another function as an argument, returns a function, or both.

### 8.2. Explain first-class functions and their importance in functional programming.

**Answer:** In JavaScript and many other programming languages, functions are considered as "first-class citizens." This means that functions can be:

- Assigned to variables.
- Passed as arguments to other functions.
- Returned from other functions as values.
- Stored in data structures like arrays and objects.

Here's a simple example demonstrating these properties:

````javascript
// Assigning a function to a variable
const greet = function(name) {
  return "Hello, " + name;
}
// Passing a function as an argument to another function
function runFunction(fn, value) {
  return fn(value);
}
runFunction(greet, 'John'); // Returns: "Hello, John"
// Returning a function from another function
function multiplier(factor) {
  return function(number) {
    return number \* factor;
  }
}
const double = multiplier(2);
double(5); // Returns: 10
// Storing function in an array
const functions = [greet, double];
````

### 8.3. What is Execution Context and Lexical Environment?

**Answer:** Generally, a function has its imaginary container or we can say some sort of context API. It provides the function with 3 things: 
- Variables declared in the function
- The functions defined in the function
- Lexical environment
This is known as Execution Context of a function.

The lexical environment is a type of information source which provides the parent function with the scope of variables it can use. For ex:

````javascript
// Assigning a function to a variable
function parent() {
  var a;
  var b;

  function child() {
    var x;
    var y;
    {rest code}
  }
}
````
Here, the lexical environment will have the information that parent function can use the variable a and b but not x and y (provides scope to the parent).

---

## 9. Storing data in browser

### A. Local storage and Session storage

### 9.1 what are the key differences between Local Storage and Session Storage?

**Answer:** Web Storage is a web API that provides two mechanisms for storing data in a web browser: Local Storage and Session Storage. The key differences are:

* Lifetime: Local Storage data persists even after the browser is closed, while Session Storage data is only available for the duration of the page session.
* Scope: Local Storage data is accessible across multiple windows and tabs from the same origin, whereas Session Storage data is limited to the current page or tab.
* Storage Limit: Local Storage typically has a larger storage limit (around 5-10 MB) compared to Session Storage (about 5-10 MB as well).

### 9.2 How do you store data in Local Storage and Session Storage using JavaScript?

**Answer:** You can use the localStorage and sessionStorage objects to store data. Here's an example of storing data in Local Storage:

`localStorage.setItem('username', 'JohnDoe');`

To store data in Session Storage, replace localStorage with `sessionStorage.`


### 9.3 How can you clear or remove data from Local Storage and Session Storage?

**Answer:** You can remove an item from storage using the removeItem method. To clear all items, you can use the clear method. For example:

Remove an item : 
`localStorage.removeItem('username');`

Clear all items : 
`localStorage.clear();`

### 9.4 Explain the security concerns associated with Web Storage.

**Answer:** Web Storage is domain-specific, meaning that data is accessible only from the same domain that stored it. However, there are security concerns related to storing sensitive information in Web Storage. Data is not encrypted, and it's vulnerable to cross-site scripting (XSS) attacks, where malicious scripts can access and modify the stored data.

### B. IndexDB

IndexedDB can be thought of as a “localStorage on steroids”. It’s a simple key-value database, powerful enough for offline apps, yet simple to use.

### 9.5 What is IndexDB, and how does it differ from Web Storage (Local Storage and Session Storage)?

**Answer:** IndexDB is a low-level JavaScript-based database for storing large amounts of structured data. It differs from Web Storage in several ways:
* Data Structure: IndexedDB stores structured data, while Web Storage stores key-value pairs.
* Storage Limit: IndexedDB typically offers a larger storage limit (often in megabytes) compared to the limited storage of Web Storage.
* API Complexity: IndexedDB has a more complex API, requiring developers to define a database schema and work with transactions.

### 9.6 How do you open a database and create an object store in IndexedDB using JavaScript?

**Answer:** You can open a database and create an object store like this:

Open a database (or create if it doesn't exist) :  

`const request = indexedDB.open('myDatabase', 1);`

Create an object store : 
```sh
request.onupgradeneeded = (event) => {
  const db = event.target.result;
  db.createObjectStore('myStore', { keyPath: 'id' });
};
```

## 10. Code Optimization

### 10.1. What is tree shaking ?

**Answer:** Tree shaking is a form of dead code elimination. It means that unused modules will not be included in the bundle during the build process and for that it relies on the static structure of ES2015 module syntax,( i.e. import and export). Initially this has been popularized by the ES2015 module bundler rollup.

### 10.2. What is the need of tree shaking ?

**Answer:** Tree Shaking can significantly reduce the code size in any application. i.e, The less code we send over the wire the more performant the application will be. For example, if we just want to create a “Hello World” Application using SPA frameworks then it will take around a few MBs, but by tree shaking it can bring down the size to just a few hundred KBs. Tree shaking is implemented in Rollup and Webpack bundlers.

### 10.3. Explain the role of the static structure of ES2015 module syntax in tree shaking. How does tree shaking leverage this structure to eliminate dead code?

**Answer:** Tree shaking relies on the static structure of ES2015 module syntax, which means that the import and export statements have a clear and static structure at compile time. During the build process, the bundler (e.g., Rollup or Webpack) analyzes the import statements to determine which modules are being used and which are not. It then eliminates the unused modules from the final bundle, resulting in smaller and more efficient code.

### 10.4. What steps can you take to optimize tree shaking in a complex JavaScript project with multiple dependencies and deep module hierarchies?

**Answer:** To optimize tree shaking in a complex project:

- Ensure all dependencies use ES2015 module syntax.
- Configure your bundler to perform tree shaking.
- Use the "sideEffects" property in your package.json to mark files or directories as side-effect free.
- Minimize the use of dynamic imports.
- Regularly audit and update your code to remove unused exports and functions.
