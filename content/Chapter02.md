# 第二章·基础

{% tooltips %}
在本章中，我们将学习编程和 JavaScript 语言的基础知识。
@@
In this first chapter, we'll learn the basics of programming and the Javascript language.
{% endtooltips %}

{% tooltips %}
编程意味着编写代码。一本书由章节、段落、句子、短语、单词，最后是标点和字母组成，类似地，程序也可以分解为越来越小的组件。目前最重要的是语句。语句类似于书中的一个句子。它本身具有结构和目的，但如果没有上下文中的其他语句，它的意义并不大。
@@
Programming means writing code. A book is made up of chapters, paragraphs, sentences, phrases, words, and finally punctuation and letters, likewise a program can be broken down into smaller and smaller components. For now, the most important is a statement. A statement is analogous to a sentence in a book. On its own, it has structure and purpose, but without the context of the other statements around it, it isn't that meaningful.
{% endtooltips %}

{% tooltips %}
语句通常（也更常见地）被称为代码行。这是因为语句往往是逐行编写的。因此，程序是从上到下、从左到右读取的。你可能想知道什么是代码（也称为源代码）。实际上，这是一个广泛的术语，既可以指整个程序，也可以指最小的部分。因此，代码行就是你程序中的一行。
@@
A statement is more casually (and commonly) known as a _line of code_. That's because statements tend to be written on individual lines. As such, programs are read from top to bottom, left to right. You might be wondering what code (also called source code) is. That happens to be a broad term which can refer to the whole of the program or the smallest part. Therefore, a line of code is simply a line of your program.
{% endtooltips %}

{% tooltips %}
下面是一个简单的示例：
@@
Here is a simple example:
{% endtooltips %}

```javascript
let hello = "Hello";
let world = "World";

// Message equals "Hello World"
let message = hello + " " + world;
```

{% tooltips %}
这段代码可以由另一个名为解释器的程序执行，它会读取代码，并按正确的顺序执行所有语句。
@@
This code can be executed by another program called an _interpreter_ that will read the code, and execute all the statements in the right order.
{% endtooltips %}

{% tooltips %}
在本章中，我们将探讨以下主题：
* [注释](#注释)
* [类型](#类型)
* [变量](#变量)
* [等式](#等式)
@@
In this chapter, we will explore following topics:
* Comments
* Equality
* Types
* Variables
{% endtooltips %}

## 注释

{% tooltips %}
注释是不会被解释器执行的语句，注释用于为其他程序员标注说明或为代码做简短的描述，从而让其他人更容易理解你的代码的作用。注释还可以用来临时禁用代码，而不影响程序的控制流程。
@@
Comments are statements that will not be executed by the interpreter, comments are used to mark annotations for other programmers or small descriptions of what code does, thus making it easier for others to understand what your code does. They are also used to temporarily disable code without affecting the program control flow.
{% endtooltips %}

{% tooltips %}
在 JavaScript 中，注释可以用两种方式编写：
@@
In JavaScript, comments can be written in two different ways:
{% endtooltips %}

{% tooltips %}
* **单行注释**：以两个正斜杠 (`//`) 开头，直到行尾的内容都会被忽略，不被 JavaScript 解释器执行。例如：
@@
* **Single-line comments**: It starts with two forward slashes (`//`) and continue until the end of the line. Anything following the slashes is ignored by the JavaScript interpreter. For example:
{% endtooltips %}

```javascript
// This is a comment, it will be ignored by the interpreter
let a = "this is a variable defined in a statement";
```

{% tooltips %}
* **多行注释**：以正斜杠和星号 (`/*`) 开头，以星号和正斜杠 (`*/`) 结尾。注释内容位于这两个符号之间，JavaScript 解释器会忽略其中的所有内容。例如：
@@
* **Multi-line comments**: It starts with a forward slash and an asterisk (`/*`) and end with an asterisk and a forward slash (`*/`). Anything between the opening and closing markers is ignored by the JavaScript interpreter. For example:
{% endtooltips %}

```javascript
/*
This is a multi-line comment,
it will be ignored by the interpreter
*/
let a = "this is a variable defined in a statement";
```

{% tooltips %}
在代码中包含注释对于维护代码质量、促进协作以及简化调试过程至关重要。通过为程序的各个部分提供上下文和解释，注释使得将来理解代码变得更加容易。因此，在代码中加入注释被视为一种有益的实践。
@@
Including comments in code is essential for maintaining code quality, enabling collaboration, and simplifying the debugging process. By providing context and explanations for various parts of the program, comments make it easier to understand the code in the future. Therefore, it is considered a beneficial practice to include comments in code.
{% endtooltips %}

## 变量

{% tooltips %}
真正理解编程的第一步是回顾代数。如果你还记得在学校学过的代数，它是从书写类似以下的术语开始的。
@@
The first step towards really understanding programming is looking back at algebra. If you remember it from school, algebra starts with writing terms such as the following.
{% endtooltips %}

```javascript
3 + 5 = 8
```

{% tooltips %}
当你引入未知数时，就开始进行计算，例如下面的 `x`：
@@
You start performing calculations when you introduce an unknown, for example, `x` below:
{% endtooltips %}

```
3 + x = 8
```
{% tooltips %}
通过移动这些，你可以确定 `x` 的值：
@@
Shifting those around you can determine `x`:
{% endtooltips %}

```javascript
x = 8 - 3
-> x = 5
```

{% tooltips %}
当你引入不止一个未知数时，你的表达式会变得更加灵活——你在使用变量：
@@
When you introduce more than one you make your terms more flexible - you are using variables:
{% endtooltips %}

```javascript
x + y = 8
```

{% tooltips %}
你可以更改 `x` 和 `y` 的值，公式依然成立：
@@
You can change the values of `x` and `y` and the formula can still be true:
{% endtooltips %}

```javascript
x = 4
y = 4
```

或者

```
x = 3
y = 5
```

{% tooltips %}
编程语言中也是如此。在编程中，变量是用于存储会变化的值的容器。变量可以保存各种类型的值，也可以保存计算结果。变量有一个`名称`和一个`值`，它们由等号 `(=)` 分隔开。然而，需要注意的是，不同的编程语言对变量名有自己的限制和约束，因为某些单词可能被保留用于语言中的特定功能或操作。
@@
The same is true for programming languages. In programming, variables are containers for values that change. Variables can hold all kinds of values and also the results of computations. Variables have a `name` and a `value` separated by an equals sign `(=)`. However, it is important to keep in mind that different programming languages have their own limitations and constraints on what can be used as variable names. This is because certain words may be reserved for specific functions or operations within the language.
{% endtooltips %}

{% tooltips %}
让我们看看它在 JavaScript 中如何工作。以下代码定义了两个变量，计算这两个变量相加的结果，并将此结果定义为第三个变量的值：
@@
Let's check out how it works in Javascript. The following code defines two variables, computes the result of adding the two, and defines this result as a value of a third variable.
{% endtooltips %}

```javascript
let x = 5;
let y = 6;
let result = x + y;
```

{% tooltips %}
在命名变量时需要遵循一些指南。它们是：

- 变量名必须以字母、下划线 `_` 或美元符号 `$` 开头。
- 在第一个字符之后，可以使用_字母_、_数字_、_下划线_或_美元符号_。
- JavaScript 区分大小写（区分大小写），因此 `myVariable`、`MyVariable` 和 `MYVARIABLE` 是三个不同的变量。
- 为了使代码易于阅读和维护，建议使用具有描述性的变量名，以准确反映其用途。
@@
There are certain guidelines that needs to be followed while  naming variables. They are

- Variable names have to start with a letter, an underscore `(_)`, or a dollar sign `($)`.
- After the first character, we can use _letters_, _numbers_, _underscores_, or _dollar_ signs.
- JavaScript distinguishes between uppercase and lowercase letters (case-sensitive), so `myVariable`, `MyVariable`, and `MYVARIABLE` are all separate variables.
- To make your code easy to read and maintain, it's recommended to use descriptive variable names that accurately reflect their purpose.
{% endtooltips %}

{% exercise %}
定义一个变量 `x` 等于 20.

{% initial %}
let x =

{% solution %}
let x = 20;

{% validation %}
assert(x == 20);

{% context %}
{% endexercise %}

**ES6版本**

{% tooltips %}
[ECMAScript 2015 或 ES2015](https://262.ecma-international.org/6.0/)，也被称为 ES6，是自 2009 年以来对 JavaScript 编程语言的重要更新。在 ES6 中，我们有三种声明变量的方式。
@@
[ECMAScript 2015 or ES2015](https://262.ecma-international.org/6.0/) also known as E6  is a significant update to the JavaScript programming language since 2009. In ES6 we have three ways of declaring variables.&#x20;
{% endtooltips %}

```javascript
var x = 5;
const y = 'Test';
let z = true;
```

{% tooltips %}
变量的声明类型取决于作用域。与 `var` 关键字不同，`var` 会定义一个全局变量或在整个函数范围内定义一个局部变量，而不考虑块级作用域。而 `let` 允许你声明的变量仅限于它们被使用的块、语句或表达式的作用域。例如：
@@
The types of declaration depend upon the scope. Unlike the `var` keyword, which defines a variable globally or locally to an entire function regardless of block scope, `let` allows you to declare variables that are limited in scope to the block, statement, or expression in which they are used. For example.
{% endtooltips %}

```javascript
function varTest(){
    var x=1;
    if(true){
        var x=2; // same variable
        console.log(x); //2
    }
    console.log(x); //2
}

function letTest(){
    let x=1;
    if(true){
        let x=2;
        console.log(x); // 2
    }
    console.log(x); // 1
}
```
{% tooltips %}
`const` 变量是不可变的，意味着它们不能被重新赋值。例如：
@@
`const` variables are immutable meaning that they are not allowed to be re-assigned.
{% endtooltips %}

```javascript
const x = "hi!";
x = "bye"; // this will occurs an error 
```

## 类型

{% tooltips %}
计算机非常复杂，能够使用比数字更复杂的变量类型。这时变量类型就派上用场了。变量有多种类型，不同的编程语言支持不同的类型。
@@
Computers are sophisticated and can make use of more complex variables than just numbers. This is where variable types come in. Variables come in several types and different languages support different types.
{% endtooltips %}

{% tooltips %}
最常见的类型有：

- **Number（数字）**：数字可以是整数（例如 `1`、`-5`、`100`）或浮点值（例如 `3.14`、`-2.5`、`0.01`）。JavaScript 没有单独的整数和浮点类型，它们都被视为数字。
- **String（字符串）**：字符串是字符序列，可以用单引号（例如 'hello'）或双引号（例如 `"world"`）表示。
- **Boolean（布尔值）**：布尔值表示真假，它们可以写为 `true` 或 `false`（不加引号）。
- **Null（空值）**：null 类型表示一个空值，意思是“没有值”，可以写为 `null`（不加引号）。
- **Undefined（未定义）**：undefined 类型表示一个未设置的值。如果一个变量已声明但未赋值，它的值就是 `undefined`。
- **Object（对象）**：对象是属性的集合，每个属性都有名称和值。你可以使用大括号 `{}` 创建一个对象，并使用名称-值对为其分配属性。
- **Array（数组）**：数组是对象的一种特殊类型，它可以保存一组项目。你可以使用方括号 `[]` 创建数组，并为其赋值列表。
- **Function（函数）**：函数是一段可以定义并按名称调用的代码块。[函数](../content/Chapter08.md) 可以接受参数（输入）并返回值（输出）。你可以使用 `function` 关键字创建一个函数。
@@
The most common types are:

* **Number**: Numbers can be integers (e.g., `1`, `-5`, `100`) or floating-point values (e.g., `3.14`, `-2.5`, `0.01`). JavaScript does not have a separate type for integers and floating-point values; it treats them both as numbers.
* **String**: Strings are sequences of characters, represented by either single quotes (e.g., `'hello'`) or double quotes (e.g., `"world"`).
* **Boolean**: Booleans represent a true or false value. They can be written as `true` or `false` (without quotes).
* **Null**: The null type represents a null value, which means "no value." It can be written as `null` (without quotes).
* **Undefined**: The undefined type represents a value that has not been set. If a variable has been declared, but has not been assigned a value, it is `undefined`.
* **Object**: An object is a collection of properties, each of which has a name and a value. You can create an object using curly braces (`{}`) and assigning properties to it using name-value pairs.
* **Array**: An array is a special type of object that can hold a collection of items. You can create an array using square brackets (`[]`) and assigning a list of values to it.
* **Function**: A function is a block of code that can be defined and then called by name. [Functions](../functions/README.md) can accept arguments (inputs) and return a value (output). You can create a function using the `function` keyword.
{% endtooltips %}

{% tooltips %}
JavaScript 是一种"_弱类型_"语言，这意味着你不需要明确声明变量的数据类型。你只需使用 `var` 关键字声明变量，解释器会根据上下文和使用的引号推断出数据类型。
@@
JavaScript is a "_loosely typed_"  language, which means that you don't have to explicitly declare what type of data the variables are. You just need to use the `var` keyword to indicate that you are declaring a variable, and the interpreter will work out what data type you are using from the context, and use of quotes.
{% endtooltips %}

{% exercise %}
Declare three variables and initialize them with the following values: `age` as a number, `name` as a string and `isMarried` as a boolean.

{% initial %}
let age =
let name = 
let isMarried =
{% solution %}
let age = 30
let name = "Cecilia"
let isMarried = true

{% validation %}
assert(typeof age === "number" && typeof name === "string" && typeof isMarried === "boolean");

{% context %}
{% endexercise %}

{% tooltips %}
`typeof` 操作符用于检查变量的数据类型。
@@
The `typeof` operator is used to checking the datatypes of a variable.
{% endtooltips %}

```javascript
typeof "John"                 // Returns "string"
typeof 3.14                   // Returns "number"
typeof NaN                    // Returns "number"
typeof false                  // Returns "boolean"
typeof [1,2,3,4]              // Returns "object"
typeof {name:'John', age:34}  // Returns "object"
typeof new Date()             // Returns "object"
typeof function () {}         // Returns "function"
typeof myCar                  // Returns "undefined" *
typeof null                   // Returns "object
```
{% tooltips %}
在 JavaScript 中，数据类型可以根据是否包含值分为两类。
@@
Data types used in JavaScript can be differentiated into two categories based on containing values.
{% endtooltips %}

{% tooltips %}
可以包含值的数据类型： 
@@
Data types that can contain values:
{% endtooltips %}

* `string`
* `number`
* `boolean`
* `object`
* `function`

{% tooltips hintStyle="info" %}
`Object`、`Date`、`Array`、`String`、`Number` 和 `Boolean` 是 JavaScript 中可用的对象类型。
@@
`Object`, `Date`, `Array`, `String`, `Number`, and `Boolean` are the types of objects available in JavaScript.
{% endtooltips %}

{% tooltips %}
不能包含值的数据类型： 
@@
Data types that cannot contain values:
{% endtooltips %}

* `null`
* `undefined`

{% tooltips %}
原始数据值是简单的数据值，没有附加的属性和方法，并且不是对象。原始数据类型是不可变的，意味着它们不能被更改。JavaScript 中有 7 种原始数据类型：
@@
A primitive data value is a simple data value with no additional properties and methods, and is not an object. They are immutable, meaning that they can't be altered. There are 7 primitive data types:
{% endtooltips %}

* string
* number
* bigint
* boolean
* undefined
* symbol
* null

{% exercise %}
Declare a variable called `person` and initialize it with an object that contains the following properties: `age` as a number, `name` as a string and `isMarried` as a boolean.

{% initial %}
let person =

{% solution %}
let person = {
  name: "Mary",
  age: 25,
  isMarried: false
};

{% validation %}
assert(typeof person.age === "number" && typeof person.name === "string" && typeof person.isMarried === "boolean");

{% context %}
{% endexercise %}


## 等式

{% tooltips %}
在编写程序时，我们经常需要确定变量与其他变量的相等性。这是通过使用相等运算符来完成的。最基本的相等运算符是 `==` 运算符。这个运算符会尽可能地判断两个变量是否相等，即使它们不是同一类型。
@@
While writing a program we frequently need to determine the equality of variables in relation to other variables. This is done using an equality operator. The most basic equality operator is the `==` operator. This operator does everything it can to determine if two variables are equal, even if they are not of the same type.
{% endtooltips %}

{% tooltips %}
例如，假设：
@@
For example, assume:
{% endtooltips %}

```javascript
let foo = 42;
let bar = 42;
let baz = "42";
let qux = "life";
```

{% tooltips %}
`foo == bar` 将评估为 `true`，而 `baz == qux` 将评估为 `false`，这符合预期。然而，尽管 `foo` 和 `baz` 类型不同，`foo == baz` 也将评估为`true`。这是因为 `==` 相等运算符在判断相等性时，会尝试将操作数强制转换为相同的类型。这与 `===` 相等运算符形成了对比。
@@
`foo == bar` will evaluate to `true` and `baz == qux` will evaluate to `false`, as one would expect. However, `foo == baz` will also evaluate to `true` despite `foo` and `baz` being different types. Behind the scenes the `==` equality operator attempts to force its operands to the same type before determining their equality. This is in contrast to the `===` equality operator.
{% endtooltips %}

{% tooltips %}
`===` 相等运算符只有在两个变量的类型相同且值也相等时，才会判断它们相等。在之前的假设下，这意味着 `foo === bar` 仍将评估为 `true`，但 `foo === baz` 现在将评估为 `false`。而 `baz === qux` 仍然会评估为 `false`。
@@
The `===` equality operator determines that two variables are equal if they are of the same type _and_ have the same value. With the same assumptions as before, this means that `foo === bar` will still evaluate to `true`, but `foo === baz` will now evaluate to `false`. `baz === qux` will still evaluate to `false`.
{% endtooltips %}

{% exercise %}
Use the `==` and `===` operator to compare the values of `str1` and `str2`.

{% initial %}
let str1 = "hello";
let str2 = "HELLO";
let bool1 = true;
let bool2 = 1;
// compare using ==
let stringResult1 =
let boolResult1 =
// compare using ===
let stringResult1 =
let boolResult2 = 
{% solution %}
let str1 = "hello";
let str2 = "HELLO";
let bool1 = true;
let bool2 = 1;
// compare using ==
let stringResult1 = str1 == str2 // false
let boolResult1 =  bool1 == bool2 // true

// compare using ===
let stringResult2 = str1 === str2 // false
let boolResult2 = bool1 === bool2 // false


{% validation %}
assert(stringResult1 === false && stringResult2 === false && boolResult1 ==true &&  boolResult2 === false );

{% context %}
{% endexercise %}