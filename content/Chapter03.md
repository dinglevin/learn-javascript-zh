# 第三章·数值

{% tooltips %}
JavaScript***只有一种数字类型*** —— 64 位浮点数。这与 Java 的 `double` 相同。与大多数其他编程语言不同的是，它没有单独的整数类型，因此 1 和 1.0 是相同的值。创建数字非常简单，可以像其他任何变量类型一样使用 `var` 关键字来创建。
@@
JavaScript has **only one type of number** – 64 bit float point. It's the same as Java's `double`. Unlike most other programming languages, there is no separate integer type, so 1 and 1.0 are the same value. Creating a number is easy, it can be done just like for any other variable type using the `var` keyword.
{% endtooltips %}

{% tooltips %}
数字可以通过常量值创建：
@@
Numbers can be created from a constant value:
{% endtooltips %}

```javascript
// This is a float:
let a = 1.2;

// This is an integer:
let b = 10;
```

{% tooltips %}
或者，从另一个变量的值创建：
@@
Or, from the value of another variable:
{% endtooltips %}

```javascript
let a = 2;
let b = a;
```
{% tooltips %}
整数的精度准确到 15 位，最大数字为 17。
@@
The precision of integers is accurate up to 15 digits and the maximum number is 17.
{% endtooltips %}

```javascript
let x = 999999999999999;   // x will be 999999999999999
let y = 9999999999999999;  // y will be 10000000000000000
```

{% tooltips %}
如果数字常量前面加上 0x，则会被解释为十六进制。
@@
The numeric constants are interpreted as hexadecimal if they are preceded by an `0x`.
{% endtooltips %}

```javascript
let z = 0xFF; // 255
```

{% tooltips %}
在本章中，我们将探讨以下主题：
* [Math类](#Math类)
* [基本运算符](#基本运算符)
* [高级运算符](#高级运算符)
@@
In this chapter, we will explore following topics:
* Math
* Basic Operators
* Advanced Operators
{% endtooltips %}

## Math类

{% tooltips %}
Math 对象允许在 JavaScript 中执行数学运算。它是静态的，没有构造函数。可以在不先创建 Math 对象的情况下使用 Math 对象的方法和属性。要访问其属性，可以使用 Math.property. 一些数学属性如下所述：
@@
The `Math` object allows performing mathematical operations in JavaScript. It is static and doesn't have a constructor. One can use method and properties of Math object without creating a Math object first. For accessing its property one can use _Math.property._ Some of the math properties are described below:
{% endtooltips %}

```javascript
Math.E; // returns Euler's number
Math.PI; // returns PI
Math.SQRT2; // returns the square root of 2
Math.SQRT1_2; // returns the square root of 1/2
Math.LN2; // returns the natural logarithm of 2
Math.LN10; // returns the natural logarithm of 10
Math.LOG2E; // returns base 2 logarithm of E
Math.LOG10E; // returns base 10 logarithm of E
```

{% tooltips %}
以下是一些数学方法的示例：
@@
Examples of some of the math methods are:
{% endtooltips %}

```javascript
Math.pow(8, 2); // 64
Math.round(4.6); // 5
Math.ceil(4.9); // 5
Math.floor(4.9); // 4
Math.trunc(4.9); // 4
Math.sign(-4); // -1
Math.sqrt(64); // 8
Math.abs(-4.7); // 4.7
Math.sin((90 * Math.PI) / 180); // 1 (the sine of 90 degrees)
Math.cos((0 * Math.PI) / 180); // 1 (the cos of 0 degrees)
Math.min(0, 150, 30, 20, -8, -200); // -200
Math.max(0, 150, 30, 20, -8, -200); // 150
Math.random(); // 0.44763808380924375
Math.log(2); // 0.6931471805599453
Math.log2(8); // 3
Math.log10(1000); // 3
```

{% tooltips %}
要访问数学方法，可以直接调用其方法，并在需要时传入参数。

| 方法             | 描述                                                                               |
| ------------------ | ------------------------------------------------------------------------------- |
| `abs(x)`           | 返回 `x` 的绝对值                                                                 |
| `acos(x)`          | 返回 `x` 的反余弦值，以弧度表示                                                     |
| `acosh(x)`         | 返回 `x` 的双曲反余弦值                                                            |
| `asin(x)`          | 返回 `x` 的反正弦值，以弧度表示                                                     |
| `asinh(x)`         | 返回 `x` 的双曲反正弦值                                                            |
| `atan(x)`          | 返回 `x` 的反正切值，值在 `-PI/2` 到 `PI/2` 之间（以弧度表示）                         |
| `atan2(y,x)`       | 返回其参数商的反正切值                                                              |
| `atanh(x)`         | 返回 `x` 的双曲反正切值                                                            |
| `crbt(x)`          | 返回 `x` 的立方根                                                                 |
| `ceil(x)`          | 返回 `x` 向上舍入到最接近的整数                                                      |
| `cos(x)`           | 返回 `x` 的余弦值，以弧度表示                                                        |
| `cosh(x)`          | 返回 `x` 的双曲余弦值                                                               |
| `exp(x)`           | 返回 `x` 的指数值                                                                  |
| `floor(x)`         | 返回 `x` 向下舍入到最接近的整数                                                       |
| `log(x)`           | 返回 `x` 的自然对数                                                                 |
| `max(x,y,z,... n)` | 返回最高的数值                                                                      |
| `min(x,y,z,... n)` | 返回最低的数值                                                                      |
| `pow(x,y)`         | 返回 `x` 的 `y` 次方                                                               |
| `random()`         | 返回介于 `0` 和 `1` 之间的数字                                                       |
| `round(x)`         | 将数字四舍五入到最接近的整数                                                          |
| `sign(x)`          | 返回 `x` 的符号，负数为 `-1`，零为 `0`，正数为 `1`                                     |
| `sin(x)`           | 返回 `x` 的正弦值，以弧度表示                                                         |
| `sinh(x)`          | 返回 `x` 的双曲正弦值                                                                |
| `sqrt(x)`          | 返回 `x` 的平方根                                                                   |
| `tan(x)`           | 返回角度的正切值                                                                     |
| `tanh(x)`          | 返回 `x` 的双曲正切值                                                                |
| `trunc(x)`         | 返回数字 `x` 的整数部分                                                              |
@@
To access maths method, one can call its methods directly with arguments wherever necessary.

| Method             | Description                                                                     |
| ------------------ | ------------------------------------------------------------------------------- |
| `abs(x)`           | Returns absolute value of `x`                                                   |
| `acos(x)`          | Returns arccosine of `x`, in radians                                            |
| `acosh(x)`         | Returns hyperbolic arccosine of `x`                                             |
| `asin(x)`          | Returns arcsine of `x`, in radians                                              |
| `asinh(x)`         | Returns hyperbolic arcsine of `x`                                               |
| `atan(x)`          | Returns arctangent of `x` as a numeric value between `-PI/2` and `PI/2` radians |
| `atan2(y,x)`       | Returns arctangent of the quotient of its arguments                             |
| `atanh(x)`         | Returns hyperbolic arctangent of `x`                                            |
| `crbt(x)`          | Returns cubic root of `x`                                                       |
| `ceil(x)`          | Returns rounded upwards to the nearest integer of `x`                           |
| `cos(x)`           | Returns consine of `x`, in radians                                              |
| `cosh(x)`          | Returns hyperbolic cosine of `x`                                                |
| `exp(x)`           | Returns exponential value of `x`                                                |
| `floor(x)`         | Returns round downwards to the nearest integer of `x`                          |
| `log(x)`           | Returns natural logarithmetic of `x`                                            |
| `max(x,y,z,... n)` | Returns number with the highest value                                           |
| `min(x,y,z,... n)` | Returns number with the lowest value                                            |
| `pow(x,y)`         | Returns value of `x` to the power of `y`                                        |
| `random()`         | Returns number between 0 and 1                                                  |
| `round(x)`         | Rounds number to the nearest `x`                                                 |
| `sign(x)`          | Returns if x is negative, `null` or positive (-1,0,1)                           |
| `sin(x)`           | Returns sine of `x`, in radians                                                   |
| `sinh(x)`          | Returns hyperbolic sine of `x`                                                    |
| `sqrt(x)`          | Returns square root of `x`                                                        |
| `tan(x)`           | Returns tangent of an angle                                                     |
| `tanh(x)`          | Returns hyperbolic tangent of `x`                                                 |
| `trunc(x)`         | Returns integer part of a number (`x`)                                            |
{% endtooltips %}

## 基本运算符

{% tooltips %}
在 JavaScript 中，运算符是用于对操作数（值和变量）执行操作的符号或关键字。例如：
@@
In JavaScript, an operator is a symbol or keyword user to perform operations on operands (values and variables). For example:
{% endtooltips %}

```javascript
2 + 3; //5
```

{% tooltips %}
这里 `+` 是一个执行加法的运算符，而 `2` 和 `3` 是操作数。
@@
Here `+` is an operator that performs addition, and `2` and `3` are operands.
{% endtooltips %}

### 运算符类型

{% tooltips %}
JavaScript 支持多种运算符，具体如下：

- [算术运算符](#算术运算符)
- [赋值运算符](#赋值运算符)
- [比较运算符](#比较运算符)
- [逻辑运算符](#逻辑运算符)
- [三元运算符](#三元运算符)
- [位运算符](#位运算符)
- [`typeof` 运算符](#`typeof` 运算符)
@@
There are various operators supported by JavaScript. They are as follows:

- Arithmetic Operators
- Assignment Operators
- Comparison Operators
- Logical Operators
- Ternary Operators
- Bitwise Operators
- `typeof` Operators
{% endtooltips %}

#### 算术运算符

{% tooltips %}
算术运算符用于对值执行数学运算。它们包括：

- [加法运算符 (+)](#加法运算符-)
- [减法运算符 (-)](#减法运算符-)
- [乘法运算符 (*)](#乘法运算符-)
- [除法运算符 (/)](#除法运算符-)
- [取余运算符 (%)](#取余运算符-)
@@
Arithmetic operators are used to perform mathematical operations on values. They include

- Addition (`+`) operator
- Subtraction (`-`) operator
- Multiplication (`*`) operator
- Division (`/`) operator
- Remainder (`%`) operator
{% endtooltips %}

##### 加法运算符 (`+`)

{% tooltips %}
加法运算符将两个数字相加。例如：
@@
The addition operator adds two numbers together. For example:
{% endtooltips %}

```javascript
console.log(1 + 2); // 3
console.log(1 + -2); // -1
```

##### 减法运算符 (`-`)

{% tooltips %}
减法运算符用于从一个数字中减去另一个数字。例如：
@@
The subtraction operator subtracts one number from another. For example:
{% endtooltips %}

```javascript
console.log(3 - 2); // 1
console.log(3 - -2); // 5
```

##### 乘法运算符 (`*`)

{% tooltips %}
乘法运算符将两个数字相乘。例如：
@@
The multiplication operator multiplies two numbers. For example:
{% endtooltips %}

```javascript
console.log(2 * 3); // 6
console.log(2 * -3); // -6
```

##### 除法运算符 (`/`)

{% tooltips %}
除法运算符将一个数字除以另一个数字。例如：
@@
The division operator divides one number by another. For example:
{% endtooltips %}

```javascript
console.log(6 / 2); // 3
console.log(6 / -2); // -3
```

##### 取余运算符 (`%`)

{% tooltips %}
取余运算符返回除法运算的余数。例如：
@@
The remainder operator returns the remainder of a division operation. For example:
{% endtooltips %}

```javascript
console.log(10 % 3); // 1
console.log(11 % 3); // 2
console.log(12 % 3); // 0
```

{% tooltips %}
JavaScript 解释器从左到右执行运算。可以像数学中一样使用括号来分隔和组合表达式：`c = (a / b) + d`
@@
The JavaScript interpreter works from left to right. One can use parentheses just like in math to separate and group expressions: `c = (a / b) + d`
{% endtooltips %}

{% tooltips hintStyle="info" %}
JavaScript 使用 `+` 运算符既用于加法也用于字符串连接。数字会相加，而字符串会连接。
@@
JavaScript uses the `+` operator for both addition and concatenation. Numbers are added whereas strings are concatenated.
{% endtooltips %}

{% tooltips %}
术语 `NaN` 是一个保留字，表示一个数字不是合法数字。当我们对非数字字符串执行算术运算时，会得到 `NaN`（非数字）。
@@
The term `NaN` is a reserved word indicating that a number is not a legal number, this arises when we perform arithmetic with a non-numeric string will result in `NaN` (Not a Number).
{% endtooltips %}

```javascript
let x = 100 / "10";
```

{% tooltips %}
`parseInt` 方法会将值解析为字符串并返回第一个整数。
@@
The `parseInt` method parses a value as a string and returns the first integer.
{% endtooltips %}

```javascript
parseInt("10"); // 10
parseInt("10.00"); // 10
parseInt("10.33"); // 10
parseInt("34 45 66"); // 34
parseInt(" 60 "); // 60
parseInt("40 years"); //40
parseInt("He was 40"); //NaN
```

{% tooltips %}
在 JavaScript 中，如果我们计算的数字超出最大可能值，它将返回 `Infinity`（无穷大）。
@@
In JavaScript, if we calculate a number outside the largest possible number it returns `Infinity`.
{% endtooltips %}

```javascript
let x = 2 / 0; // Infinity
let y = -2 / 0; // -Infinity
```

{% exercise %}
Use the math operators +, -, \*, /, and % to perform the following operations on `num1` and `num2`.

{% initial %}
let num1 = 10;
let num2 = 5;

// Add num1 and num2.
let addResult =
// Subtract num2 from num1.
let subtractResult =
// Multiply num1 and num2.
let multiplyResult =
// Divide num1 by num2.
let divideResult =
// Find the remainder num1 is divided by num2.
let reminderResult =

{% solution %}
let num1 = 10;
let num2 = 5;

// Add num1 and num2.
let addResult = (num1 + num2);
// Subtract num2 from num1.
let subtractResult = (num1 - num2);
// Multiply num1 and num2.
let multiplyResult = (num1 \* num2);
// Divide num1 by num2.
let divideResult = (num1 / num2);
// Find the remainder num1 is divided by num2.
let reminderResult = (num1 % num2);

{% validation %}
assert(addResult === 15 && subtractResult === 5 && multiplyResult === 50 && divideResult === 2 && reminderResult === 0 );

{% context %}
{% endexercise %}

#### 赋值运算符

{% tooltips %}
赋值运算符用于将值赋给变量或计算被赋值的值。_可以链接赋值运算符，以将单个值赋给多个变量。_ 它们包括赋值运算符 (`=`) 和复合赋值运算符，如 `+=`、`-=`、`*=` 和 `/=`。
@@
Assignment operators are used to assign values to variables or evaluates the assigned value. _Chaining the assignmentoperator is possible in order to assign a single value to multiple values._ They includes the assignment(`=`) operator and compound assignment operators like `+=`, `-=`, `*=` and `/=`.
{% endtooltips %}

##### 赋值运算符(`=`)

{% tooltips %}
该运算符用于将右侧的值赋给左侧的变量。 例如：
@@
This operator is used to assign the value on the right side to the variable on the left side. For examples:
{% endtooltips %}

```javascript
let x = 10; //Assigns the value 10 to the variable x.
```

##### 复合赋值运算符

{% tooltips %}
这些运算符将算术运算与赋值操作结合在一起。它们是执行运算后将结果重新赋值给变量的快捷方式。例如：
@@
These operator combine the arithmetic operation with the assignment operation. They are shortcuts for performing an operation and then assigning the result back to the variable. For example:
{% endtooltips %}

###### 加法赋值(`+=`)

{% tooltips %}
它将右侧的值加到变量上，并将结果重新赋值给该变量。
@@
It adds the value on the right side to the variable and assigns the result back to the variable.
{% endtooltips %}

###### 减法赋值(`-=`)

{% tooltips %}
它将右侧的值从变量中减去，并将结果重新赋值给该变量。
@@
It subtracts the value on the right side from the variable and assigns the result back to the variable.
{% endtooltips %}

###### 乘法赋值(`*=`)

{% tooltips %}
它将变量乘以右侧的值，并将结果重新赋值给该变量。
@@
It multiplies the variable by the value on the right side and assigns the result back to the variable.
{% endtooltips %}

###### 除法赋值(`/=`)

{% tooltips %}
它将变量除以右侧的值，并将结果重新赋值给该变量。
@@
It divides the variable by the value on the right side and assigns the result back to the variable.
{% endtooltips %}

###### 取模/余数赋值(`%=`)

{% tooltips %}
它计算变量除以右侧值后的余数，并将结果重新赋值给该变量。
@@
It computes the remainder when the variable is divided by the value on the right side and assigns the result back to the variable.
{% endtooltips %}

```javascript
let a = 10;
a += 5; // Equivalent to a = a + 5; (a becomes 15)
a -= 3; // Equivalent to a = a - 3; (a becomes 12)
a *= 2; // Equivalent to a = a * 2; (a becomes 24)
a /= 4; // Equivalent to a = a / 4; (a becomes 6)
a %= 5; // Equivalent to a = a % 5; (a becomes 1)
```

#### 比较运算符

{% tooltips %}
比较运算符用于比较两个值或表达式，并返回一个 boolean 结果，即 `true` 或 `false`。这些运算符通常用于条件语句中，以进行决策或评估条件。
@@
Comparison operators are used to compare two values or expressions and return a `boolean` result, which is either `true` or `false`. These operators are commonly used in conditional statements to make decision or evaluate 
conditions.
{% endtooltips %}

##### 等于 (`==`)

{% tooltips %}
此运算符检查左右两边的值是否相等。如果它们相等，则返回 `true`，否则返回 `false`。它不考虑数据类型。
@@
This operator checks if the values on the left and right sides are equal. If they are equal, it returns `true` otherwise, it returns false. It does not consider data types.
{% endtooltips %}

```javascript
5 == 5; // true
"5" == 5; // true (implicit type conversion)
```

##### 不等于 (`!=`)

{% tooltips %}
此运算符检查左右两边的值是否不相等。如果它们不相等，则返回 `true`，否则返回 `false`。
@@
This operator checks if the values on the left and right sides are not equal. If they are not equal, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
5 != 3; // true
"5" != 5; // false (implicit type conversion)
```

##### 严格等于 (`===`)

{% tooltips %}
此运算符检查左右两边的值是否相等并且数据类型是否相同。如果值和数据类型都匹配，则返回 `true`，否则返回 `false`。
@@
This operator checks if the values on the left and right sides are equal and have the same data type. If both the value and data type match, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
5 === 5; // true
"5" === 5; // false (different data types)
```

##### 严格不等于 (`!==`)

{% tooltips %}
此运算符检查左右两边的值是否不相等或数据类型是否不同。如果它们不相等或数据类型不同，则返回 `true`，否则返回 `false`。
@@
This operator checks if the values on the left and right sides are not equal or have different data types. If they are not equal or have different data types, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
5 !== "5"; // true (different data types)
5 !== 5; // false
```

##### 大于 (`>`)

{% tooltips %}
此运算符检查左边的值是否大于右边的值。如果左边的值更大，则返回 `true`，否则返回 `false`。
@@
This operator checks if the value on the left is greater than the value on the right. If the left value is greater, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
8 > 5; // true
3 > 10; // false
```

##### 小于 (`<`)

{% tooltips %}
此运算符检查左边的值是否小于右边的值。如果左边的值更小，则返回 `true`，否则返回 `false`。
@@
This operator checks if the value on the left is less than the value on the right. If the left value is less, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
3 < 5; // true
8 < 2; // false
```

##### 大于或等于 (`>=)`

{% tooltips %}
此运算符检查左边的值是否大于或等于右边的值。如果左边的值大于或等于，则返回 `true`，否则返回 `false`。
@@
This operator checks if the value on the left is greater than or equal to the value on the right. If the left value is greater or equal, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
8 >= 5; // true
3 >= 8; // false
```

##### 小于或等于 (`<=`)

{% tooltips %}
此运算符检查左边的值是否小于或等于右边的值。如果左边的值小于或等于，则返回 `true`，否则返回 `false`。
@@
This operator checks if the value on the left is less than or equal to the value on the right. If the left value is less or equal, it returns `true` otherwise, it returns `false`.
{% endtooltips %}

```javascript
3 <= 5; // true
8 <= 2; // false
```

#### 逻辑运算符

{% tooltips %}
逻辑运算符用于对布尔值或表达式执行逻辑运算。这些运算符允许您组合或操作布尔值，以做出决策或评估复杂的条件。
@@
Logical operators are used to perform logical operations on Boolean values or expressions. These operators allow you to combine or manipulate Boolean values to make decisions or evaluate complex conditions.
{% endtooltips %}

##### 逻辑与 (`&&`)

{% tooltips %}
逻辑与运算符在两个操作数都为 true 时返回 true。如果至少有一个操作数为 `false`，则返回 `false`。
@@
The logical AND operator returns `true` if both operands are `true`. If at least one of the operands is `false`, it returns `false`.
{% endtooltips %}

```javascript
true && true; // true
true && false; // false
false && true; // false
false && false; // false
```

##### 逻辑或 (`||`)

{% tooltips %}
逻辑或运算符在至少有一个操作数为 `true` 时返回 `true`。只有当两个操作数都为 `false` 时才返回 `false`。
@@
The logical OR operator returns `true` if at least one of the operands is `true`. It returns `false` only if both operands are `false`.
{% endtooltips %}

```javascript
true || true; // true
true || false; // true
false || true; // true
false || false; // false
```

##### 逻辑非 (`!`)

{% tooltips %}
逻辑非运算符对操作数的值进行取反。如果操作数为 false，则返回 true；如果操作数为 `true`，则返回 `false`。
@@
The logical NOT operator negates the value of an operand. It returns `true` if the operand is `false`, and it returns `false` if the operand is `true`.
{% endtooltips %}

```javascript
!true; // false
!false; // true
```

#### 三元运算符

{% tooltips %}
三元运算符有三个操作数。它是 `if/else` 的简化形式。
@@
Ternary operator has three operands. It is the simplified operator of `if/else`.
{% endtooltips %}

{% tooltips %}
这是 `if-else` 条件的简写形式。
@@
It is the short form of the `if-else` condition.
{% endtooltips %}

{% tooltips %}
**语法**
@@
**Syntax**
{% endtooltips %}

```js
Y =  ? A : B
If the condition is true then Y = A otherwise Y = B
```

```javascript
let isEven = 8 % 2 === 0 ? "Even" : "Odd";
console.log(isEven); // "Even"
```

#### 位运算符

{% tooltips %}
位运算符用于操作二进制数字的单个位。它们在位级别上执行操作，在需要控制或分析低级数据的情况下非常有用。
@@
Bitwise operators are used to manipulate individual bits of binary numbers. They perform operations at the bit level, 
{% endtooltips %}which is especially useful in situations where you need to control or analyze low-level data.

##### 位与 (`&`)

{% tooltips %}
该运算符比较两个数字的每一位，只有当两个数字的对应位都是 1 时返回 1。其他所有位都设置为 0。
@@
This operator compares each bit of two numbers and returns 1 for each bit that is 1 in both numbers. All other bits are set to 0.
{% endtooltips %}

```javascript
1010 & 1100; // 1000
```

##### 位或 (`|`)

{% tooltips %}
该运算符比较两个数字的每一位，只要至少有一个数字的对应位是 1，就返回 1。
@@
This operator compares each bit of two numbers and returns 1 for each bit that is 1 in at least one of the numbers.
{% endtooltips %}

```javascript
1010 | 1100; // 1110
```

##### 位异或 (`^`)

{% tooltips %}
该运算符比较两个数字的每一位，如果某一位在一个数字中是 1 而在另一个数字中不是，则返回 1。
@@
This operator compares each bit of two numbers and returns 1 for each bit that is 1 in one number but not in both.
{% endtooltips %}

```javascript
1010 ^ 1100; // 0110
```

##### 位非 (`~`)

{% tooltips %}
该运算符翻转一个数字的所有位。它将每个 0 变为 1，每个 1 变为 0。
@@
This operator inverts (flips) all the bits of a number. It changes each 0 to 1 and each 1 to 0.
{% endtooltips %}

```javascript
~1010; // 0101
```

##### 左移 (`<<`)

{% tooltips %}
该运算符将一个数字的位向左移动指定的位数，用 0 填充移入的位。
@@
This operator shifts the bits of a number to the left by a specified number of positions, filling the shifted-in positions with 0.
{% endtooltips %}

```javascript
1010 << 2; // 101000 (shifted left by 2 positions)
```

##### 右移 (`>>`)

{% tooltips %}
该运算符将一个数字的位向右移动指定的位数。移入的位根据最左边的位（符号位）填充。
@@
This operator shifts the bits of a number to the right by a specified number of positions. The shifted-in positions are filled based on the leftmost bit (sign bit).
{% endtooltips %}

```javascript
1010 >> 2; // 0010 (shifted right by 2 positions)
```

#### `typeof` 运算符

{% tooltips %}
它返回操作数的类型，JavaScript 中可能存在的类型包括：`undefined`、`Object`、`boolean`、`number`、`string`、`symbol` 和 `function`。
@@
It returns the operand type, The possible types that exist in javascript are `undefined`, `Object`, `boolean`, `number`, `string`, `symbol`, and `function`.
{% endtooltips %}

```javascript
let value1 = 42;
let value2 = "Hello, World!";
let value3 = true;
let value4 = null;

console.log(typeof value1); // "number"
console.log(typeof value2); // "string"
console.log(typeof value3); // "boolean"
console.log(typeof value4); // "object" (Note: `typeof null` returns "object" due to historical reasons)
```

## 高级运算符

{% tooltips %}
当运算符没有括号时，它们的应用顺序由运算符的优先级决定。乘法 (`*`) 和除法 (`/`) 的优先级高于加法 (`+`) 和减法 (`-`)。
@@
When operators are put together without parenthesis, the order in which they are applied is determined by the _precedence_ of the operators. Multiplication `(*)` and division `(/)` has higher precedence than addition `(+)` and subtraction `(-)`.
{% endtooltips %}

```javascript
// multiplication is done first, which is then followed by addition
let x = 100 + 50 * 3; // 250
// with parenthesis operations inside the parenthesis are computed first
let y = (100 + 50) * 3; // 450
// operations with the same precedences are computed from left to right
let z = 100 / 50 * 3;
```

{% tooltips %}
在编写程序时，可以使用一些高级数学运算符。以下是一些主要的高级数学运算符：
@@
Several advanced math operators can use be used while writing program. Here is a list of some of the main advanced math operators:
{% endtooltips %}

{% tooltips %}
* **取模运算符 (`%`)**：取模运算符返回除法运算的余数。例如：
@@
* **Modulo operator (`%`)**: The modulo operator returns the remainder of a division operation. For example:
{% endtooltips %}

```javascript
console.log(10 % 3); // 1
console.log(11 % 3); // 2
console.log(12 % 3); // 0
```

{% tooltips %}
* **幂运算符** (`**`)：幂运算符将一个数提升到另一个数的幂次方。这是一个较新的运算符，不是所有浏览器都支持，因此可能需要使用 Math.pow 函数来替代。例如：
@@
* **Exponentiation operator** (`**`): The exponentiation operator raises a number to the power of another number. It is a newer operator and is not supported in all browsers, so you may need to use the `Math.pow` function instead. For example:
{% endtooltips %}

```javascript
console.log(2 ** 3); // 8
console.log(3 ** 2); // 9
console.log(4 ** 3); // 64
```

{% tooltips %}
* **递增运算符 (`++`)**：递增运算符将一个数加一。它可以作为前缀（在操作数前）或后缀（在操作数后）使用。例如：
@@
* **Increment operator (`++`)**: The increment operator increments a number by one. It can be used as a prefix (before the operand) or a postfix (after the operand). For example:
{% endtooltips %}

```javascript
let x = 1;
x++; // x is now 2
++x; // x is now 3
```

{% tooltips %}
* **递减运算符 (`--`)**：递减运算符将一个数减一。它可以作为前缀（在操作数前）或后缀（在操作数后）使用。例如：
@@
* **Decrement operator (`--`)**: The decrement operator decrements a number by one. It can be used as a prefix (before the operand) or a postfix (after the operand). For example:
{% endtooltips %}

```javascript
let y = 3;
y--; // y is now 2
--y; // y is now 1
```

{% tooltips %}
* **Math 对象**：`Math` 对象是 JavaScript 中的内置对象，它提供了数学函数和常量。您可以使用 `Math` 对象的方法执行高级数学操作，例如求一个数的平方根、计算一个数的正弦值或生成一个随机数。例如：
@@
* **Math object**: The `Math` object is a built-in object in JavaScript that provides mathematical functions and constants. You can use the methods of the `Math` object to perform advanced math operations, such as finding the square root of a number, calculating the sine of a number, or generating a random number. For example:
{% endtooltips %}

```javascript
console.log(Math.sqrt(9)); // 3
console.log(Math.sin(0)); // 0
console.log(Math.random()); // a random number between 0 and 1
```

{% tooltips %}
这些只是 JavaScript 中可用的高级数学运算符和函数的几个例子。在编写程序时，您可以使用更多其他运算符来执行高级数学操作。
@@
These are just a few examples of the advanced math operators and functions available in JavaScript. There are many more that you can use to perform advanced math operations while writing program.
{% endtooltips %}

{% exercise %}
Use the following advanced operators to perform operations on `num1` and `num2`.

{% initial %}
let num1 = 10;
let num2 = 5;

// ++ operator to increment the value of num1.
const result1 =
// -- operator to decrement the value of num2.
const result2 =
//  += operator to add num2 to num1.
const result3 =
// -= operator to subtract num2 from num1.
const result4 =

{% solution %}
let num1 = 10;
let num2 = 5;

// ++ operator to increment the value of num1.

num1++;
const result1 = num1; // 11
// -- operator to decrement the value of num2.
num2--;
const result2 = num2; // 4
//  += operator to add num2 to num1.
num1 += num2;
const result3 = num1 // 15
// -= operator to subtract num2 from num1.
num1 -= num2;
const result4 = num1 // 11

{% validation %}
assert(result1 === 11 && result2 === 4 && result3 === 15 && result4 === 11 );

{% context %}
{% endexercise %}

### 空值合并运算符 `??`

{% tooltips %}
`nullish` 合并运算符在第一个参数不是 `null/undefined` 时返回该参数，否则返回第二个参数。它用两个问号 `??` 表示。`x ?? y` 的结果是：

* 如果 `x` 已定义，则返回 `x`，
* 如果 `y` 未定义，则返回 `y`。
@@
The `nullish` coalescing operator returns the first argument if it's not `null/undefined`, else the second one. It is written as two question marks `??`. The result of `x ?? y` is:

* if `x` is defined, then `x`,
* if `y` isn’t defined, then `y`.
{% endtooltips %}

{% tooltips hintStyle="info" %}
这是语言中的一项新功能，可能需要使用 polyfills 来支持旧浏览器
@@
It's a recent addition to the language and might need polyfills to support old browsers
{% endtooltips %}
