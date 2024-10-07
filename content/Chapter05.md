# 第五章·条件逻辑

A condition is a test for something. Conditions are very important for programming, in several ways:

First of all, conditions can be used to ensure that your program works, regardless of what data you throw at it for processing. If you blindly trust data, you’ll get into trouble and your programs will fail. If you test that the thing you want to do is possible and has all the required information in the right format, that won’t happen, and your program will be a lot more stable. Taking such precautions is also known as programming defensively.

The other thing conditions can do for you is allow for branching. You might have encountered branching diagrams before, for example when filling out a form. Basically, this refers to executing different “branches” (parts) of code, depending on if the condition is met or not.

In this chapter, we'll learn the basics of conditional logic in JavaScript, including the following topics:

* [If](./if.md)
* [Else](./else.md)
* [Switch](./switch.md)
* [Comparators](./comparators.md)
* [Concatenate](./concatenate.md)

# If

The easiest condition is an if statement and its syntax is `if(condition){ do this … }`. The condition has to be true for the code inside the curly braces to be executed. You can for example test a string and set the value of another string dependent on its value as described below.

```javascript
let country = "France";
let weather;
let food;
let currency;

if (country === "England") {
  weather = "horrible";
  food = "filling";
  currency = "pound sterling";
}

if (country === "France") {
  weather = "nice";
  food = "stunning, but hardly ever vegetarian";
  currency = "funny, small and colourful";
}

if (country === "Germany") {
  weather = "average";
  food = "worst thing ever";
  currency = "funny, small and colourful";
}

let message =
  "this is " +
  country +
  ", the weather is " +
  weather +
  ", the food is " +
  food +
  " and the " +
  "currency is " +
  currency;

console.log(message);
// 'this is France, the weather is nice, the food is stunning, but hardly ever vegetarian and the currency is funny, small and colourful'
```

## Nested If-Else

In JavaScript, you can use nested `if-else` statements to create more complex conditional logic.

### Basic Syntax

```javascript
if (condition1) {
  // Code to execute when condition1 is true
} else {
  if (condition2) {
    // Code to execute when condition1 is false and condition2 is true
  } else {
    // Code to execute when both condition1 and condition2 are false
  }
}
```

The following program determines a person's student status based on their age and prints a corresponding message.

```JavaScript
let age = 20;
let isStudent = true;

if (age >= 18) {
  if (isStudent) {
    console.log("You are an adult student.");
  } else {
    console.log("You are an adult, but not a student.");
  }
} else {
  console.log("You are not an adult.");
}

// Output: You are an adult student.
```

This program checks for rain, temperature, and snow to provide weather advice.

```JavaScript
let temperature = 25;
let isRaining = true;
let isSnowing = false;

if (isRaining) {
  console.log("It's raining. Don't forget your umbrella.");

  if (temperature < 10) {
    console.log("And it's cold. You might need a coat too.");
  }
} else if (isSnowing) {
  console.log("It's snowing. Be prepared for slippery roads.");
} else {
  console.log("No rain or snow. Enjoy the weather!");
}

// Output: It's raining. Don't forget your umbrella.
```

This program checks a person's age, prior driving experience, and written test status to determine eligibility for a driver's license.

```JavaScript
let age = 19;
let hasPriorExperience = true;
let hasPassedWrittenTest = true;

if (age >= 18) {
  if (hasPriorExperience) {
    console.log("Congratulations! You are eligible for a driver's license.");
  } else {
    console.log("Sorry, you need prior driving experience to get a driver's license.");
  }
} else {
  console.log("Sorry, you must be 18 or older to apply for a driver's license.");

  if (hasPassedWrittenTest) {
    console.log("You've passed the written test, but you need to wait until you're 18 to apply.");
  } else {
    console.log("You need to pass the written test first and wait until you're 18 to apply.");
  }
}

// Output: Congratulations! You are eligible for a driver's license.

```

# Else

There is also an `else` clause that will be applied when the first condition isn’t `true`. This is very powerful if you want to react to any value, but single out one in particular for special treatment.

```javascript
let umbrellaMandatory;

if (country === "England") {
  umbrellaMandatory = true;
} else {
  umbrellaMandatory = false;
}
```

The `else` clause can be joined with another `if`. Let's remake the example from the previous article.

```javascript
if (country === "England") {
  ...
} else if (country === "France") {
  ...
} else if (country === "Germany") {
  ...
}
```

{% exercise %}
From the following values write a conditional statement that checks if `num1` is greater than `num2`. If it is, assign "num1 is greater than num2" to the `result` variable. If it is not, assign "num1 is less than or equal to num2".

{% initial %}
let num1 = 10;
let num2 = 5;
let result;

// check if num1 is greater than num2
if( condition ) {

}else {

}
{% solution %}
let num1 = 10;
let num2 = 5;
let result;

// check if num1 is greater than num2
if (num1 > num2) {
  result = "num1 is greater than num2";
} else {
  result = "num1 is less than or equal to num2";
}

{% validation %}
assert(result == "num1 is greater than num2" );

{% context %}
{% endexercise %}

# Switch

A `switch` is a conditional statement that performs actions based on different conditions. It uses strict ( `===` ) comparison to match the conditions and executes the code blocks of matched condition.  The syntax of the `switch` expression is shown below.

```javascript
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

The expression is evaluated once and is compared with each case. If a match is found, then the associated code block is executed if not `default` code block is executed. The `break` keyword stops the execution and can be placed anywhere. In its absence, the next condition is evaluated even if the conditions are not matched.&#x20;

An example of getting a weekday name based on the switch condition is shown below.&#x20;

```javascript
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
     day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
}
```

In multiple matching cases, the **first** matching value is selected, if not the default value is selected. In the absence of default and no matching case, the program continues to the next statement(s) after switch conditions.&#x20;

{% exercise %}
From the following values write a `switch` statement that checks the value of dayOfWeek. If dayOfWeek is "Monday", "Tuesday", "Wednesday", "Thursday", or "Friday", assign "It's a weekday" to the result variable. If `dayOfWeek` is "Saturday" or "Sunday", assign "It's the weekend" to the result.

{% initial %}
let dayOfWeek = "Monday";
let result;
// check if it's a weekday or the weekend
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
{% solution %}
let dayOfWeek = "Monday";
let result;
// check if it's a weekday or the weekend
switch (dayOfWeek) {
  case "Monday":
  case "Tuesday":
  case "Wednesday":
  case "Thursday":
  case "Friday":
    result = "It's a weekday";
    break;
  case "Saturday":
  case "Sunday":
    result = "It's the weekend";
    break;
  default:
    result = "Invalid day of the week";
    break;
}
{% validation %}
assert(result == "It's a weekday" );

{% context %}
{% endexercise %}

# Comparators

Lets now focus on the conditional part:

```javascript
if (country === "France") {
    ...
}
```

The conditional part is the variable `country` followed by the three equal signs (`===`). Three equal signs tests if the variable `country` has both the correct value (`France`) and also the correct type (`String`). You can test conditions with double equal signs, too, however a conditional such as `if (x == 5)` would then return true for both `var x = 5;` and `var x = "5";`. Depending on what your program is doing, this could make quite a difference. It is highly recommended as a best practice that you always compare equality with three equal signs (`===` and `!==`) instead of two (`==` and `!=`).

Other conditional tests:

* `x > a`: is x bigger than a?
* `x < a`: is x less than a?
* `x <= a`: is x less than or equal to a?
* `x >=a`: is x greater than or equal to a?
* `x != a`: is x not a?
* `x`: does x exist?

## Logical Comparison

In order to avoid the if-else hassle, simple logical comparisons can be utilised.

```javascript
let topper = marks > 85 ? "YES" : "NO";
```

In the above example, `?` is a logical operator. The code says that if the value of marks is greater than 85 i.e. `marks > 85` , then `topper = YES` ; otherwise `topper = NO` . Basically, if the comparison condition proves true, the first argument is accessed and if the comparison condition is false, the second argument is accessed. This shorthand operator is also known as the `ternary operator` as it takes three operands.

```javascript
condition ? expression1 : expression2
```

# Concatenate

Furthermore, you can concatenate different conditions with "`or`" or “`and`” statements, to test whether either statement is true, or both are true, respectively.

In JavaScript “or” is written as `||` and “and” is written as `&&`.

Say you want to test if the value of x is between 10 and 20. You could do that with a condition stating:

```javascript
if (x > 10 && x < 20) {
    ...
}
```

If you want to make sure that country is either “England” or “Germany” you use:

```javascript
if (country === "England" || country === "Germany") {
    ...
}
```

> **Note**: Just like operations on numbers, conditions can be grouped using parenthesis, ex: `if ( (name === "John" || name === "Jennifer") && country === "France")`.
