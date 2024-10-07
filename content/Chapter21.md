# 第二十一章·实战练习

In this chapter we will be performing exercises to test our knowledge in JavaScript. The exercises that we will be performing are listed below:

* [Concatenation](./concatenation.md)
* [Conditional Statements](./conditional-statements.md)
* [Constants](./constants.md)
* [Console](./console.md)
* [FizzBuzz Problem](./fizzbuzz-problem.md)
* [Functions](./functions.md)
* [Get the Titles!](./get-the-titles.md)
* [Multiplication](./multiplication.md)
* [Objects](./objects.md)
* [User Input Variables](./user-input-variables.md)


# Concatenation

In any programming language, string concatenation simply means appending one or more strings to another string. For example, when strings "_World_" and "_Good Afternoon_" are concatenated with string "_Hello_", they form the string "_Hello World, Good Afternoon_". We can concatenate a string in several ways in JavaScript.

### Example:

```javascript
const icon = "👋";

// using template Strings
`hi ${icon}`;

// using join() Method
["hi", icon].join(" ");

// using concat() Method
"".concat("hi ", icon);

//  using + operator
"hi " + icon;

// RESULT
// hi 👋
```

### 📝 Task:

- [ ] Write a program to set the values for `str1`and `str2` so the code prints '_Hello World_' to the console.

- [ ] Write a program that prompt user to enter their first name(`first_name`) and last name(`last_name`). Then, use string concatenation to create and display their full name(`full_name`).

- [ ] Write a program that prompt user to enter their name. Then, use string concatenation to create a greeting message that include their name. For examples: `Good morning, Aman`.

### 💡 Hints:

- Visit the [concatenation](../strings/concat.md) chapter of strings for more info about string concatenation.
Console output: {{ output.name }}
{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Conditional Statements

Conditional logic is vital in programming as it makes sure that the program works regardless of what data you throw in and also allows branching. This exercise is about the implementation of various conditional logic in real-life problems.

### 📝 Task:

- [ ] Write a program to create a prompt "_How many km is left to go?_" and based on the user and the following conditions, print the results in the `console`.
  - If there are more than 100 km left to go, print: `"You still have a bit of driving left to go"`.
  - If there are more than 50 km, but less or equal to 100 km, print: `"I'll be there in 5 minutes"`.
  - If there are less than or equal to 50 km, print: `"I'm parking. I'll see you right now"`.
- [ ] Write a program that checks whether a person is eligible to vote or not based on their age.

  - If the age of user is 18 or older then print `You are eligible to vote`
  - If the age of user is less than 18 then print `You aren't eligible to vote`.

    **_Note: `age` can be between `1` to `100`._**

### 💡 Hints:

- Visit the [conditional logic](../conditional/) chapter to understand how to use conditional logic and conditional statements.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Constants

Constants were introduced in ES6(2015), and use a `const` keyword. Variables that are declared with `const` cannot be reassigned or redeclared.&#x20;

### Example:

```javascript
const VERSION = "1.2";
```

### 📝 Task:

- [ ] Run the program mentioned below and fix the error that you see in the console. Make sure that the code result is `0.9` when it is fixed in the console.

  ```javascript
  const VERSION = "0.7";
  VERSION = "0.9";
  console.log(VERSION);
  ```

- [ ] Write a program that prompts user to enter a temperature in _degrees Celsius_, then use constant `CONVERSION_FACTOR` which equals to `9/5` to convert to _degrees Fahrenheit_.

  ```javascript
  const CONVERSION_FACTOR = 9 / 5;

  /* Start your code from here*/
  ```

### 💡 Hints:

- Visit the [Variables](../basics/variables.md) chapter for more info about const and also look for "_TypeError assignment to constant variable_" in search engines to learn a fix.&#x20;

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Console

In JavaScript, we use `console.log()` to write a message (the content of a variable, a given string, etc.) in `console`. It is mainly used for debugging purposes, ideally to leave a trace of the content of variables during the execution of a program.

### Example:

```javascript
console.log("Welcome to Learn JavaScript Beginners Edition");
let age = 30;
console.log(age);
```

## Math with console
You can also write math equation in `console` in order to know the answer to an expression.

### Example:
```js
console.log("What's the age a decade later?");
let age = 30;
console.log(age + 10);
//returns 40 in the console
```

## Booleans in console
Another useful way developers use console is to check wether something is true or false. For instance in the example below you can check wether the age of a person being equal to 45 is true or false. 

### Example:
```js
console.log("Are they 50 years old?");
let age = 30;
console.log(age === 50);
//result: false
```

### 📝 Tasks:

*  Write a program to print `Hello World` on the console. Feel free to try other things as well!
* Write a program to print variables to the `console`.&#x20;
  1. Declare a variable  `animal` and assign the dragon value to it.
  2. Print the `animal` variable to the `console`.
* Write a program to print the number `45` with a math expression of your choice. (Bonus if one of the numbers is a variable!)

* Write a program in the console that checks if the amounts of eggs is more than `12`.
  1. Declare a variable `eggs` and assign a number of your choice to it
  2. Call the `eggs` variable in the `console` and use the correct operator to see if the number assigned to `eggs` is greater that 12
      * If the number of eggs is greater, it should print `true`, if not then it should print `false`





### 💡 Hints:

* Visit the [variable](../basics/variables.md) chapter to understand more about variables.
* Visit the [operators](https://javascript.sumankunwar.com.np/en/numbers/operators.html) page to know the possible operators you can use.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# FizzBuzz Problem

The _FizzBuzz_ problem is one of the commonly asked questions, here one has to print _Fizz_ and _Buzz_ upon some conditions.

### 📝 Tasks:

* [ ] Write a program to print all the numbers between 1 to 100 in such a way that the following conditions are met.
  * For multiples of 3, instead of the number, print `Fizz`.
  * For multiples of 5, print `Buzz`.
  * For numbers that are multiples of both 3 and 5, print `FizzBuzz`.

    ```javascript
    /
    1  
    2  
    Fizz  
    4  
    Buzz  
    Fizz  
    7  
    8  
    Fizz  
    Buzz  
    11  
    Fizz  
    13  
    14  
    FizzBuzz  
    16  
    ....
    ....
    98  
    Fizz  
    Buzz  
    /
    ```

### 💡 Hints:

* Visit the [loops](../loops/) chapter to understand how the loop works.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Functions

A function is a block of code designed to perform a specific task and executed when "something" invokes it. More info about functions can be found in the[ functions](../functions/) chapter.

### 📝 Task:

- [ ] Write a program to create a function named `isOdd`that passes a number `45345` as an argument and determines whether the number is odd or not.

- [ ] Call this function to get the result. The result should be in a boolean format and should return `true` in `console`.&#x20;

- [ ] Write a program to create a function named `calculateRectangleArea` that takes two parameters `width` and `height` of the rectange and should return `area` of the rectangle.

### 💡 Hints:

- Visit the [functions](../functions/) chapter to understand functions and how to create them.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Get the Titles!

The _Get the Titles!_ problem is an interesting problem where we have to get the title from a list of books. This is a good exercise for the implementation of arrays and objects.

### 📝 Tasks:

Given an array of objects that represent books with an author.

```javascript
const books = [
  {
    title: "Eloquent JavaScript, Third Edition",
    author: "Marijn Haverbeke"
  },
  {
    title: "Practical Modern JavaScript",
    author: "Nicolás Bevacqua"
  }
]
```

* [ ] Write a program to create a function `getTheTitles` that takes the array and returns the array of title and print its value in the `console`.

### 💡 Hints:

* Visit the [arrays](../arrays/) and [objects](../objects/) chapter to understand how the array and object work.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Multiplication

In JavaScript, we can perform the multiplication of two numbers by using the asterisk `(*)` arithmetic operators.&#x20;

### Example:

```javascript
let resultingValue = 3 * 2;
```

Here, we stored the product of `3 * 2` into a `resultingValue` variable.

### 📝 Tasks:

- [ ] Write a program to store the product of `23` times `41` and print its value.

- [ ] Write a program that generates a multiplication table for a specific number. The program should take a number as input and then display the multiplication table for that number, from 1 to 10.

### 💡 Hints:

- Visit the [Basic Operators](../numbers/operators.md) chapter to understand the mathematical operations.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# Objects

Objects are the collection of `key`, `value` pairs and each pair of key-value are known as a property. Here, the property of the `key` can be a `string` whereas its `value` can be of any value.

### 📝 Tasks:

Given a Doe family that includes two members, where each member's information is provided in form of an object.&#x20;

```javascript
let person = {
    name: "John",                    //String
    lastName: "Doe",
    age: 35,                         //Number
    gender: "male",
    luckyNumbers: [ 7, 11, 13, 17], //Array
    significantOther: person2       //Object, 
};

let person2 = {
    name: "Jane",
    lastName: "Doe",
    age: 38,
    gender: "female",
    luckyNumbers: [ 2, 4, 6, 8],
    significantOther: person
};

let family = {
    lastName: "Doe",
    members: [person, person2]       //Array of objects
};
```

* [ ] Find a way to print the name of the first member of the Doe family in a `console`.
* [ ] Change the fourth  `luckyNumbers` of  the second member of the Doe family to `33`.
* [ ] Add a new member to the family by creating a new  person  (`Jimmy` `Doe`, `13`, `male`, `[1, 2, 3, 4]`, `null`) and update the member list.
* [ ] Print the `SUM` of the lucky numbers of Doe family in the `console`.&#x20;

### 💡 Hints:

* Visit the [objects](../objects/) chapter to understand how the object work.
* You can get `luckyNumbers` from each person object inside the family object.
* Once you get each array just loop over it adding every element and then add each sum of the 3 family members.

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}

# User Input Variables

In JavaScript, we can take input from users and use it as a variable. One doesn't need to know their value to work with them.

### 📝 Tasks:

* [ ] Write a program to take input from a user and add `10` to it, and print its result.

### 💡 Hints:

* The content of a variable is determined by the user's inputs. The `prompt()` method saves the input value as a string.
* You will need to make sure that the string value is converted into an integer for calculations.&#x20;
* Visit the [Basic Operators](../numbers/operators.md) chapter for the type conversion of `string` to `int`.&#x20;

{% if output.name == "website" %}
{% aceeditor compilerTitle="Try it!" %}
{% endaceeditor %}
{% endif %}
