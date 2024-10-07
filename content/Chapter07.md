# 第七章·循环

Loops are repetitive instructions where one variable in the loop changes. Loops are handy, if you want to run the same code over and over again, each time with a different value.

Instead of writing:

```javascript
doThing(cars[0]);
doThing(cars[1]);
doThing(cars[2]);
doThing(cars[3]);
doThing(cars[4]);
```

You can write:

```javascript
for (var i = 0; i < cars.length; i++) {
  doThing(cars[i]);
}
```

In this chapter, we are going to discuss the following topics:
* [For](./for.md)
* [While](./while.md)
* [Do...While](./dowhile.md)
* [Continue](./continue.md)
* [Break](./break.md)

## For

The easiest form of a loop is the for statement. This one has a syntax that is similar to an if statement, but with more options:

### Syntax

The syntax of `for` loop in javascript is given below

```javascript
for (initialization; end condition; change) {
    // do it, do it now
}
```

### Explanation:

- In the `initialization` part, executed before the first iteration, initialize your loop variable
- In the `end codition` part, put a condition that may be checked before each iteration. The moment the condition becomes `false`, the loop ends.
- In the `change` part, tell the program how to update the loop variable.
  Let's see how to execute the same code ten-times using a `for` loop:

```javascript
for (let i = 0; i < 10; i = i + 1) {
  // do this code ten-times
}
```

> _**Note**_: `i = i + 1` can be written `i++`.

## `for...in` loop

To loop through the enumerable properties of an object `for in` loop can be used. For each distinct property, JavaScript executes the specified statements.

### Syntax

```javascript
for (variable in object) {
  // iterate each property in the object
}
```

### Example

Let use suppose we have following object:

```javascript
const person = {
  fname: "John",
  lname: "Doe",
  age: 25,
};
```

Then, with the help of `for in` loop we can iterate over the `person` object to access it property like `fname`, `lname` and `age` as shown below.

```javascript
let info = "";
for (let x in person) {
  console.log(person[x]);
}
```

The output of above code snippet will be:

```javascript
John
Doe
25
```

> **Note: The iterable objects such as `Arrays`, `Strings`, `Maps`, `NodeLists` can be looped using `for in` statement.&#x20;**

```javascript
// Example with Arrays
const myArray = [1, 2, 3, 4, 5];
for (const item of myArray) {
  console.log(item);
}

// Example with Strings
const myString = "Hello, World!";
for (const char of myString) {
  console.log(char);
}

// Example with Maps
const myMap = new Map();
myMap.set("name", "John");
myMap.set("age", 30);

for (const [key, value] of myMap) {
  console.log(key, value);
}

// Example with NodeLists (HTML elements)
const paragraphs = document.querySelectorAll("p");
for (const paragraph of paragraphs) {
  console.log(paragraph.textContent);
}
```

## `for...of` loop

The `for...of` loop was introduced in the later versions of **[JavaScript ES6](../es6-concepts/README.md)**. The `for...of` statement executes a loop that operates on a sequence of values sourced from an iterable objects such as `Array`, `String`, `TypedArray`, `Map`, `Set`, `NodeList`(and other DOM collections).

### Syntax

The syntax of the `for...of` loop is:

```javascript
for (element of iterable) {
  //body of for...of
}
```

Here,

- **iterable** - an iterable object
- **element** - items in the iterable

In plain English, you can read the above code as: “for every element in the iterable, run the body of the loop”.

### Examples

Let use suppose we have following object:

```javascript
const person = ["John Doe", "Albert", "Neo"];
```

Then, with the help of `for of` loop we can iterate over the `person` object to access it individual element as shown below.

```javascript
let info = "";
for (let x of person) {
  console.log(x);
}
```

The output of above code snippet will be:

```javascript
John Doe
Albert
Neo
```

The use of `for...of` loop with string, maps and nodelist are given below:

```js
// Example with Strings
const text = "Hello, World!";
for (const char of text) {
  console.log(char);
}

// Example with Maps
const person = new Map();
person.set("name", "John");
person.set("age", 30);
for (const [key, value] of person) {
  console.log(key, value);
}

// Example with NodeLists (HTML elements)
const paragraphs = document.querySelectorAll("p");
for (const paragraph of paragraphs) {
  console.log(paragraph.textContent);
}
```

# While

While loops repetitively execute a block of code as long as a specified condition is true. It provides a way to automate repetitive tasks and perform iterations based on the condition's evaluation.

```javascript
while (condition) {
  // do it as long as condition is true
}
```

For example, the loop in this example will repetitively execute its block of code as long as the variable `i` is less than `5`:

```javascript
var i = 0,
x = "";
while (i < 5) {
  x = x + "The number is " + i;
  i++;
}
```

{% hint style="warning" %}
&#x20;Be careful to avoid infinite looping if the condition is always true!
{% endhint %}

# Do...While

The `do...while` statement creates a loop that executes specified bloc statement until the test condition evaluates to be false. The condition is evaluated after executing the block. The syntax for `do... while` is

```javascript
do {
  // statement
} while (expression);
```

Lets for example see how to print numbers less than 10 using `do...while` loop:

```javascript
var i = 0;
do {
  document.write(i + " ");
  i++; // incrementing i by 1
} while (i < 10);
```

> _**Note**_: `i = i + 1` can be written `i++`.

# Continue 

The `continue` statement in JavaScript is a control flow statement used to skip the current iteration of a loop and continue with the next iteration. It allows you to bypass specific code within a loop under certain conditions. This document provides an overview of the `continue` statement in JavaScript, its syntax, common use cases, and best practices.

## Syntax

In JavaScript, the `continue` statement is used within loops. The syntax is straightforward:

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        console.log("Skipping 3.");
        continue;
    }
    console.log(`Current value of i: ${i}`);
}
```

## Break

The loop ends when the condition specified for the loop becomes false. However we can end any loop forcibly by using the break statement.

### Syntax

The syntax of `break` in javascript is given below

```javascript
for (initialization; endCondition; change) {
    if(conditionForBreaking){
        break;
    }
}
```

### Explanation:

- inside the for loop whenever the condition `conditionForBreaking` is satisfied the control reaches outside the for loop and the loop end.


### Example

- Let's suppose we have an array of numbers and need to print the first occurrence of a number divisible by 5. We can use the `break` statement to achieve this:

```javascript
const arr = [4, 7, 9, 11, 45, 23, 15, 87];

for(let i = 0; i < arr.length; i++){
    if(arr[i]%5 == 0){
        console.log(arr[i]);
        break;
    }
}
//This code will print 45 which is the first occurence of a number divisible by 5
```
- Break statement can also be used inside `while` loop.

```javascript
const arr = [4, 7, 9, 11, 45, 23, 15, 87];
let i = 0;
while(i < arr.length){
    if(arr[i]%5 == 0){
        console.log(arr[i]);
        break;
    }
    i++;
}
//This code will also print 45 which is the first occurence of a number divisible by 5
```
