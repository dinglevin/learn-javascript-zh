# 第八章·函数

Functions are one of the most powerful and essential notions in programming. Functions like mathematical functions perform transformations, they take input values called **arguments** and **return** an output value. &#x20;

Functions can be created in two ways: using `function declaration` or `function expression` . The _function name_ can be omitted in `function expression` making it an `anonymous function`.  Functions, like variables, must be declared. Let's declare a function `double` that accepts an _argument_ called `x` and **returns** the double of x :

```javascript
// an example of a function declaration
function double(x) {
  return 2 * x;
}
```

> _Note:_ the function above **may** be referenced before it has been defined.

Functions are also values in JavaScript; they can be stored in variables (just like numbers, strings, etc ...) and given to other functions as arguments :

```javascript
// an example of a function expression
let double = function (x) {
  return 2 * x;
};
```

> _Note:_ the function above **may not** be referenced before it is defined, just like any other variable.

{% hint style="info" %}
&#x20;A callback is a function passed as an argument to another function.
{% endhint %}

An arrow function is a compact alternative to traditional functions which has some semantic differences with some limitations. These function doesn't have their own bindings to `this`, `arguments` and `super`, and cannot be used as constructors. An example of an arrow function:

```javascript
const double =  (x) =>  2 * x;
```

{% hint style="warning" %}
The `this` keyword in the arrow function represents the object that defined the arrow function.&#x20;
{% endhint %}

In this chapter, we will explore following topics:
* [Closures](./for-each.md)
* [High Order Functions](./higher-order.md)
* [Recursive Functions](./recursive-functions.md)
* [Set Interval](./set-interval.md)
* [Set Timeout](./set-timeout.md)
* [This Keyword](./this-keyword.md)
* [Rest Operator](./rest-operator.md)
* [Hoisting](./hoisting.md)
* [Getters and Setters](./getters-setters.md)

# Closures

In JavaScript, closures are a fundamental and powerful concept that plays a crucial role in the language. Understanding closures is essential for writing clean, efficient, and maintainable code. In this chapter, we'll explore what closures are, how they work, and why they are important in JavaScript.

## What are Closures?

A closure is a function that retains access to variables from its containing (enclosing) lexical scope even after the outer function has finished execution. In simpler terms, a closure "closes over" variables, preserving their values, and allows inner functions to access them.

## How Closures Work

Closures in JavaScript are created when a function is defined within another function and references variables from the outer function. Here's a step-by-step explanation of how closures work:

1. **Function Definition**: A function is defined within another function.

2. **Variable Reference**: The inner function references variables from the outer function.

3. **Creation of a Closure**: When the inner function is created, it forms a closure, capturing the variables it references.

4. **Access to Enclosing Scope**: The inner function can still access and use the variables from the outer function, even after the outer function has finished executing.

## Practical Example

Let's illustrate closures with a practical example:

```javascript
function outerFunction() {
  const outerVariable = 'I am from the outer function';
  
  function innerFunction() {
    console.log(outerVariable);
  }
  
  return innerFunction;
}

const closureFunction = outerFunction(); // Creates a closure
closureFunction(); // Logs "I am from the outer function"
```

In this example, `outerFunction` defines `outerVariable`, and `innerFunction` accesses `outerVariable` within its scope. When `outerFunction` is invoked and `closureFunction` is assigned the value it returns, it creates a closure that retains access to `outerVariable`. Later, when `closureFunction` is called, it still has access to `outerVariable`, even though `outerFunction` has completed execution.

## Use Cases for Closures

Closures have various practical use cases in JavaScript, including:

- **Data Encapsulation**: Closures can be used to encapsulate and protect data, making it inaccessible from the outside. This is a fundamental concept in many design patterns.

- **Function Factories**: Closures allow the creation of factory functions that generate functions with specific behaviors.

- **Private Variables**: Closures enable the creation of private variables and methods within objects, keeping certain data hidden from external code.

- **Callback Functions**: Callbacks often involve closures to maintain context and data between asynchronous operations.

Closures are a powerful feature in JavaScript that allows functions to retain access to variables from their containing scope. Understanding closures is essential for writing clean and efficient code. They are commonly used in various design patterns and provide solutions for data encapsulation, function factories, and more.

Closures can be both a powerful tool and a potential source of memory leaks if not used wisely. Therefore, it's crucial to grasp the concept and use it judiciously in your JavaScript code.

---

# Higher order

Higher order functions are functions that manipulate other functions. For example, a function can take other functions as arguments and/or produce a function as its return value. Such _fancy_ functional techniques are powerful constructs available to you in JavaScript and other high-level languages like [python](https://www.python.org/), [lisp](https://common-lisp.net/), etc.

We will now create two simple functions, `add_2` and `double`, and a higher order function called `map`. `map` will accept two arguments, `func` and `list` (its declaration will therefore begin `map(func,list)`), and return an array. `func` (the first argument) will be a function that will be applied to each of the elements in the array `list` (the second argument).

```javascript
// Define two simple functions
let add_2 = function (x) {
  return x + 2;
};
let double = function (x) {
  return 2 * x;
};

// map is cool function that accepts 2 arguments:
//  func    the function to call
//  list    a array of values to call func on
let map = function (func, list) {
  let output = []; // output list
  for (idx in list) {
    output.push(func(list[idx]));
  }
  return output;
};

// We use map to apply a function to an entire list
// of inputs to "map" them to a list of corresponding outputs
map(add_2, [5, 6, 7]); // => [7, 8, 9]
map(double, [5, 6, 7]); // => [10, 12, 14]
```

The functions in the above example are simple. However, when passed as arguments to other functions, they can be composed in unforeseen ways to build more complex functions.

For example, if we notice that we use the invocations `map(add_2, ...)` and `map(double, ...)` very often in our code, we could decide we want to create two special-purpose list processing functions that have the desired operation baked into them. Using function composition, we could do this as follows:

```javascript
process_add_2 = function (list) {
  return map(add_2, list);
};
process_double = function (list) {
  return map(double, list);
};
process_add_2([5, 6, 7]); // => [7, 8, 9]
process_double([5, 6, 7]); // => [10, 12, 14]
```

Now let's create a function called `buildProcessor` that takes a function `func` as input and returns a `func`-processor, that is, a function that applies `func` to each input in list.

```javascript
// a function that generates a list processor that performs
let buildProcessor = function (func) {
  let process_func = function (list) {
    return map(func, list);
  };
  return process_func;
};
// calling buildProcessor returns a function which is called with a list input

// using buildProcessor we could generate the add_2 and double list processors as follows:
process_add_2 = buildProcessor(add_2);
process_double = buildProcessor(double);

process_add_2([5, 6, 7]); // => [7, 8, 9]
process_double([5, 6, 7]); // => [10, 12, 14]
```

Let's look at another example. We'll create a function called `buildMultiplier` that takes a number `x` as input and returns a function that multiplies its argument by `x` :

```javascript
let buildMultiplier = function (x) {
  return function (y) {
    return x * y;
  };
};

let double = buildMultiplier(2);
let triple = buildMultiplier(3);

double(3); // => 6
triple(3); // => 9
```

# Recursive Functions

In JavaScript, a recursive function is a function that calls itself in order to solve a problem. Recursion is a powerful concept that can be used to solve complex problems by breaking them down into smaller, more manageable subproblems. This document provides an overview of recursive functions in JavaScript, their syntax, common use cases, and best practices.

## Syntax

A recursive function typically has the following structure:

```javascript
function recursiveFunction(params) {
  // Base case: the simplest scenario
  if (/* base case condition */) {
    // return a value or perform an action
  } else {
    // Recursive case: call the function with modified parameters
    return recursiveFunction(modifiedParams);
  }
}
```
Common Use Cases
Recursive functions are often used to solve problems that can be divided into smaller, similar subproblems. Here are some common use cases:

**Calculating Factorials**:

A recursive function can be used to calculate the factorial of a number.

```javascript
function factorial(n) {
  if (n === 0) {
    return 1; // Base case
  } else {
    return n * factorial(n - 1); // Recursive case
  }
}

factorial(5); // Returns 120
```
**Fibonacci Sequence**:
The Fibonacci sequence can be calculated using recursion.

```javascript
function fibonacci(n) {
  if (n <= 1) {
    return n; // Base cases: F(0) = 0, F(1) = 1
  } else {
    return fibonacci(n - 1) + fibonacci(n - 2); // Recursive case
  }
}

fibonacci(5); // Returns 5
```

Recursive functions are a valuable tool in JavaScript for solving problems that involve repetitive subtasks. When used correctly, they can lead to elegant and efficient solutions.

# Set Interval
The `setInterval` method is used to call a function and add a delay time to it, in milliseconds,  before the function will run again. For example, if you're making a function that generates a random color, you can use `setInterval()` to say how long the computer has to wait before the function runs again and generates another color. This is useful in making functions repeat. 

The first parameter in the method is the name of the function for which you're setting an interval. The second parameter specifies the duration of the interval. You can also add additional parameters if you want to pass arguments to the function.

As another simple example, let's create a function called `repeatSaying` where it says "And again!" every 2 seconds in the [console](https://javascript.sumankunwar.com.np/en/exercises/console.html). 

```js
function repeatSaying() {
console.log("And again");
}
//when called, it generates in the console: "And again!"

setInterval(repeatSaying, 2000);
//calls the function every 2 seconds


```
You can also add parameters of a function when you use set interval. Continuing on with the previous example let's add an ellipsis to the console statement, to show that it repeats. First we'll add a parameter called `el` which is short for ellipse. Next we'll add a `+` followed by calling are parameter `el` to show that the value of the parameter comes after. Finally in set interval let's add a comma `,` followed by a string for the value of the ellipse parameter, we'll put `"..."`.

```js
function repeatSaying(el) {
console.log("And again!" + el);
}

setInterval(repeatSaying, 2000, "...");
//When it runs, it'll repeat the saying "And again!..."
```

As you can see from this example, after you put the function and interval for the function, you can set the values of the function parameters inside set interval. 




## Clear Interval
You can use the `clearInterval()` method to remove a set interval with a specefic variable name. As an example based on the previous one let's store set interval into a variable named `intervalTime`, however, right after our variable we'll call it inside clear interval by writing `clearInterval(intervalTime).`

```js
function repeatSaying(el) {
console.log("And again!" + el);
}

var interval = setInterval(repeatSaying, 2000, "...");

clearInterval(interval);
//The clear Interval method stops setInterval
```

When this code is run, you'll see that there is no output. This is because `setInterval` was the only thing calling the `repeatSaying` function, but since it was removed by `clearInterval` it's no longer is called. Even if it was called seperately using `repeatSaying()` it would only run once because clear Interval stops it from repeating.

# Set Timeout
The `setTimeout` global method is used to add a delay (in milliseconds) before a function is ran. 

For instance, in this example after "Ready..." is written in the console, the function `start()` has to wait 3 seconds before running.

```js
console.log("Ready...");

function start() {
console.log("go!!");
}

setTimeout(start, 3000);

//Output: "Ready..." then after 3 seconds, "go!!"
```

# Clear Timeout
The `clearTimeout` global method is used to remove any `setTimeout()` methods that are stored in variables. For instance, let's change our last example by storing `setTimeout()` in a variable
```js
console.log("Ready...");

function start() {
console.log("go!!");
}

let timeBeforeStart = setTimeout(start, 3000);

clearTimeout(timeBeforeStart);
// Stops the function as a whole from running
```

## Understanding the `this` Keyword in JavaScript

The `this` keyword in JavaScript refers to the object it belongs to. It has different values depending on where it is used: in a method, alone, in a function, in an event, etc.

### `this` in Global Context

In the global execution context (outside of any function), `this` refers to the global object, which is `window` in browsers.

```javascript
console.log(this); // Output: Window {...}
```

### `this` in Object Methods

When used in an object method, `this` refers to the object the method belongs to.

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return `${this.firstName} ${this.lastName}`;
    }
};

console.log(person.fullName()); // Output: John Doe
```

### `this` in Constructor Functions

In a constructor function, `this` refers to the newly created instance.

```javascript
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}

const person1 = new Person("Jane", "Smith");
console.log(person1.firstName); // Output: Jane
```

### `this` in Arrow Functions

Arrow functions do not have their own `this`. Instead, `this` is lexically inherited from the outer function where the arrow function is defined.

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        const getFullName = () => `${this.firstName} ${this.lastName}`;
        return getFullName();
    }
};

console.log(person.fullName()); // Output: John Doe
```

### `this` in Event Handlers

In event handlers, `this` refers to the element that received the event.

```html
<button id="myButton">Click me</button>
<script>
    document.getElementById("myButton").addEventListener("click", function() {
        console.log(this); // Output: <button id="myButton">Click me</button>
    });
</script>
```

### Changing `this` with `call`, `apply`, and `bind`

You can explicitly set the value of `this` using `call`, `apply`, and `bind`.

#### `call` Method

The `call` method calls a function with a given `this` value and arguments provided individually.

```javascript
function greet() {
    console.log(`Hello, ${this.name}`);
}

const person = { name: "Alice" };
greet.call(person); // Output: Hello, Alice
```

#### `apply` Method

The `apply` method calls a function with a given `this` value and arguments provided as an array.

```javascript
function greet(greeting) {
    console.log(`${greeting}, ${this.name}`);
}

const person = { name: "Bob" };
greet.apply(person, ["Hi"]); // Output: Hi, Bob
```

#### `bind` Method

The `bind` method creates a new function that, when called, has its `this` keyword set to the provided value.

```javascript
function greet() {
    console.log(`Hello, ${this.name}`);
}

const person = { name: "Charlie" };
const greetPerson = greet.bind(person);
greetPerson(); // Output: Hello, Charlie
```

### Conclusion

Understanding the `this` keyword is crucial for writing effective JavaScript code. Its value depends on the context in which it is used, and it can be explicitly set using `call`, `apply`, and `bind`.

## Understanding the Rest Operator for Functions in JavaScript

The rest operator (`...`) in JavaScript allows you to represent an indefinite number of arguments as an array. It is particularly useful in function definitions to handle multiple parameters without explicitly specifying them.

### Syntax

The rest operator is used by prefixing three dots (`...`) before the parameter name in a function definition.

### Example of Using the Rest Operator

Here's a basic example of using the rest operator in a function:

```javascript
function sum(...numbers) {
    return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3)); // Output: 6
console.log(sum(4, 5, 6, 7)); // Output: 22
```

In this example, the `sum` function can accept any number of arguments, which are then combined into an array called `numbers`.

### Combining Rest Operator with Other Parameters

You can use the rest operator in combination with other parameters, but it must be the last parameter in the function definition.

```javascript
function greet(greeting, ...names) {
    return `${greeting}, ${names.join(" and ")}!`;
}

console.log(greet("Hello", "Alice", "Bob")); // Output: Hello, Alice and Bob!
console.log(greet("Hi", "Charlie", "Dave", "Eve")); // Output: Hi, Charlie and Dave and Eve!
```

In this example, the `greet` function takes a fixed `greeting` parameter and a variable number of `names`.

### Rest Operator in Arrow Functions

The rest operator can also be used in arrow functions:

```javascript
const multiply = (...numbers) => numbers.reduce((acc, curr) => acc * curr, 1);

console.log(multiply(2, 3)); // Output: 6
console.log(multiply(4, 5, 6)); // Output: 120
```

### Practical Use Cases

1. **Handling Variable Arguments**: Functions that need to handle a variable number of arguments, such as mathematical operations or string manipulations.
2. **Combining Arrays**: Functions that need to combine multiple arrays into one.
3. **Event Handlers**: Functions that handle events with varying numbers of arguments.

### Example of Combining Arrays

Here's an example of using the rest operator to combine arrays:

```javascript
function combineArrays(...arrays) {
    return arrays.flat();
}

console.log(combineArrays([1, 2], [3, 4], [5, 6])); // Output: [1, 2, 3, 4, 5, 6]
```

### Conclusion

The rest operator is a powerful feature in JavaScript that allows functions to handle an indefinite number of arguments efficiently. By using the rest operator, you can write more flexible and concise functions that can adapt to various input scenarios.

## Understanding Hoisting for Functions in JavaScript

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compile phase. This means that you can use functions and variables before they are declared in the code.

### Function Hoisting

In JavaScript, function declarations are hoisted to the top of their containing scope. This allows you to call a function before it is defined in the code.

### Example of Function Hoisting

Here's an example to illustrate function hoisting:

```javascript
console.log(greet()); // Output: Hello, World!

function greet() {
    return "Hello, World!";
}
```

In this example, the `greet` function is called before it is defined, but it works because the function declaration is hoisted to the top of the scope.

### Function Expressions and Hoisting

Unlike function declarations, function expressions are not hoisted. This means that you cannot call a function expression before it is defined.

### Example of Function Expression

Here's an example to illustrate the difference:

```javascript
console.log(greet()); // Output: TypeError: greet is not a function

var greet = function() {
    return "Hello, World!";
};
```

In this example, the `greet` function is defined as a function expression, and calling it before the definition results in an error because the variable `greet` is hoisted, but its assignment is not.

### Hoisting with `let` and `const`

Variables declared with `let` and `const` are also hoisted, but they are not initialized. This means that accessing them before their declaration results in a `ReferenceError`.

### Example with `let` and `const`

```javascript
console.log(greet); // Output: ReferenceError: Cannot access 'greet' before initialization

let greet = function() {
    return "Hello, World!";
};
```

In this example, the `greet` variable is hoisted, but it is not initialized, resulting in a `ReferenceError` when accessed before its declaration.

### Conclusion

Understanding hoisting is crucial for writing predictable and bug-free JavaScript code. Function declarations are hoisted, allowing them to be called before they are defined, while function expressions are not hoisted, leading to potential errors if called before their definition. Variables declared with `let` and `const` are hoisted but not initialized, resulting in `ReferenceError` if accessed before their declaration.

## Understanding Getters and Setters in JavaScript

Getters and setters in JavaScript are special methods that provide a way to access and update the properties of an object. They allow you to control how a property is accessed and modified, adding a layer of abstraction and encapsulation.

### What are Getters and Setters?

- **Getters**: Methods that get the value of a specific property.
- **Setters**: Methods that set the value of a specific property.

### Defining Getters and Setters

You can define getters and setters using the `get` and `set` keywords within an object literal or a class.

### Example with Object Literals

Here's an example of defining getters and setters in an object literal:

```javascript
let person = {
    firstName: "John",
    lastName: "Doe",
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    set fullName(name) {
        [this.firstName, this.lastName] = name.split(" ");
    }
};

console.log(person.fullName); // Output: John Doe
person.fullName = "Jane Smith";
console.log(person.firstName); // Output: Jane
console.log(person.lastName); // Output: Smith
```

### Example with Classes

Here's an example of defining getters and setters in a class:

```javascript
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    }

    set fullName(name) {
        [this.firstName, this.lastName] = name.split(" ");
    }
}

let person = new Person("John", "Doe");
console.log(person.fullName); // Output: John Doe
person.fullName = "Jane Smith";
console.log(person.firstName); // Output: Jane
console.log(person.lastName); // Output: Smith
```

### Benefits of Using Getters and Setters

1. **Encapsulation**: Control how properties are accessed and modified.
2. **Validation**: Add validation logic when setting a property.
3. **Computed Properties**: Create properties that are computed based on other properties.

### Example of Validation

Here's an example of adding validation logic in a setter:

```javascript
class User {
    constructor(username) {
        this._username = username;
    }

    get username() {
        return this._username;
    }

    set username(name) {
        if (name.length < 3) {
            console.error("Username must be at least 3 characters long.");
        } else {
            this._username = name;
        }
    }
}

let user = new User("jsmith");
console.log(user.username); // Output: jsmith
user.username = "jo"; // Output: Username must be at least 3 characters long.
console.log(user.username); // Output: jsmith
```

### Conclusion

Getters and setters provide a powerful way to manage object properties in JavaScript. By using them, you can add validation, encapsulation, and computed properties, making your code more robust and maintainable.
