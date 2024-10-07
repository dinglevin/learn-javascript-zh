# 第四章·字符串

JavaScript strings share many similarities with string implementations in other high-level languages. They represent text-based messages and data. In this course, we will cover the basics, including how to create new strings and perform common operations on them.

Here is an example of a string:

```
"Hello World"
```

String indexes are zero-based, meaning that starting position of the first character at `0` followed by others in incremental order. Various methods are supported by string and return a new value. These methods are described below.

| Name                 | Description                                                                            |
| -------------------- | -------------------------------------------------------------------------------------- |
| `charAt()`           | Returns character at specified index                                                   |
| `charCodeAt()`       | Returns Unicode character at specified index                                           |
| `concat()`           | Returns two or more combined strings                                                   |
| `constructor`        | Returns string's constructor function                                                  |
| `endsWith()`         | Checks if a string ends with a specified value                                         |
| `fromCharCode()`     | Returns Unicode values as characters                                                   |
| `includes()`         | Checks if a string contains with a specified value                                     |
| `indexOf()`          | Returns the index of its first occurrence                                               |
| `lastIndexOf()`      | Returns the index of its last occurrence                                                |
| `length`             | Returns the length of the string                                                       |
| `localeCompare()`    | Compares two strings with locale                                                       |
| `match()`            | Matches a string against a value or regular expression                                 |
| `prototype`          | Used to add properties and method of an object                                         |
| `repeat()`           | Returns new string with number of copies specified                                     |
| `replace()`          | Returns a string with values replaced by a regular expression or a string with a value |
| `search()`           | Returns an index based on a string's match against a value or regular expression       |
| `slice()`            | Returns a string containing part of a string                                           |
| `split()`            | Splits string into array of substrings                                                 |
| `startsWith()`       | Checks strings beginning against specified character                                     |
| `substr()`           | Extracts part of string, from start index                                              |
| `substring()`        | Extracts part of string, between two indices                                           |
| `toLocalLowerCase()` | Returns string with lowercase characters using host's locale                           |
| `toLocalUpperCase()` | Returns string with uppercase characters using host's locale                           |
| `toLowerCase()`      | Returns string with lowercase characters                                               |
| `toString()`         | Returns string or string object as string                                              |
| `toUpperCase()`      | Returns string with uppercase characters                                               |
| `trim()`             | Returns string with removed whitespaces                                                |
| `trimEnd()`          | Returns string with removed whitespaces from end                                       |
| `trimStart()`        | Returns string with removed whitespaces from start                                     |
| `valueOf()`          | Returns primitive value of string or string object                                     |


In this chapter, we will explore following topics:
* [CharAt](./charAt.md)
* [Concat](./concat.md)
* [Create](./create.md)
* [Length](./length.md)
* [Replace](./replace.md)
* [Split](./split.md)
* [Substring](./substring.md)

# CharAt

The `str.charAt()` method returns the character at the given index of the string index holds the array element position.
* using the `charAt()` method
* using the template literal `(``)` (introduced in [ES6](../es6-concepts/template-literals.md))

The `charAt()` method takes in:

* **arguments**: The only argument to this function is the index in the string from where the single character is to be extracted. 

* **index**: The range of this index is between `0` and length `–1`. If no index is specified then the first character of the string is returned as `0` is the default index used for this function. 

* **return value** : Returns a single character located at the index specified as the argument to the function. If the index is out of range, then this function returns an empty string.

```javascript
//Example 1:
function func() {
	// Original string
	let str = 'JavaScript is object oriented language';

	// Finding the character at given index
	let value = str.charAt(0);
	let value1 = str.charAt(4);
	console.log(value);
	console.log(value1);
}
func();

//Output
j
s

//Example 2: 
function func() {

	// Original string
	let str = 'JavaScript is object oriented language';

	// Finding the character at given index
	let value = str.charAt(9);
	console.log(value);
}
func();


//Output
t
```

# Concatenation

Concatenation involves adding two or more strings together, creating a larger string containing the combined data of those original strings.  The concatenation of a string appends one or more strings to another string.  This is done in JavaScript using the following ways:

* using the  **`+`** operator
* using the `concat()` method
* using the array `join()` method
* using the template `(``)` literal (introduced in [ES6](../es6-concepts/template-literals.md))

The string `concat()` method accepts the list of strings as parameters and returns a new string after concatenation i.e. combination of all the strings. Whereas the array `join()` method is used to concatenate all the elements present in an array by converting them into a single string.&#x20;

The template literal  uses backtick `(``)` and provides an easy way to create multiline strings and perform string interpolation. An expression can be used inside the backtick using `$` sign and curly braces `${expression}`.

```javascript
const icon = '👋';
// using template Strings
`hi ${icon}`;

// using join() Method
['hi', icon].join(' ');

// using concat() Method
''.concat('hi ', icon);

//  using + operator
'hi ' + icon;
// hi 👋
```

# Creation

Strings can be defined by enclosing the text in single quotes or double quotes:

```javascript
// Single quotes can be used
let str = "Our lovely string";

// Double quotes as well
let otherStr = "Another nice string";
```

In Javascript, Strings can contain UTF-8 characters:

```
"中文 español English हिन्दी العربية português বাংলা русский 日本語 ਪੰਜਾਬੀ 한국어";
```

You can also use the `String` constructor to create a string object:

```javascript
const stringObject = new String('This is a string');
```

However, it is generally not recommended to use the `String` constructor to create strings, as it can cause confusion between string primitives and string objects. It is usually better to use string literals to create strings.

You can also use template literals to create strings. Template literals are strings that are enclosed in backticks `(``)` and can contain placeholders for values. Placeholders are denoted with the `` `${}` `` syntax.

```javascript
const name = 'John';
const message = `Hello, ${name}!`;
```

Template literals can also contain multiple lines and can include any expression inside the placeholders.

{% hint style="warning" %}
Strings can not be subtracted, multiplied, or divided.
{% endhint %}

{% exercise %}
Use a template literal to create a string that includes the values of `name` and `age`. The string should have the following format: "My name is John and I am 25 years old.".

{% initial %}
let name = "John";
let age = 25;

// My name is John and I am 25 years old.
let result =  
{% solution %}
let name = "John";
let age = 25;

// My name is John and I am 25 years old.
let result = `My name is ${name} and I am ${age} years old.`

{% validation %}
assert(result == "My name is John and I am 25 years old.");

{% context %}
{% endexercise %}

# Length

It's easy in Javascript to know how many characters are in a string using the property `.length`. The `length` property returns the number of characters in the string, including spaces and special characters.

```javascript

let size = "Our lovely string".length;
console.log(size);
// size: 17

let emptyStringSize = "".length
console.log(emptyStringSize);
// emptyStringSize: 0

```

The length property of an empty string is `0`.&#x20;

{% hint style="warning" %}
The `length` property is a read-only property, so you cannot assign a new value to it.
{% endhint %}

# Replace

The `replace` method allows us to replace a character, word, or sentence with a string. For example.

```javascript
let str = "Hello World!";
let new_str = str.replace("Hello", "Hi");

console.log(new_str);

// Result: Hi World!
```

{% hint style="warning" %}
To replace a value on all instances of a [regular expression](../regular-expression.md) with a `g` modifier is set.
{% endhint %}

It searches for a string for a value or a regular expression and returns a new string with the value(s) replaced. It doesn't change the original string. Let's see the global case-insensitive replacement example.

```javascript
let text = "Mr Blue has a blue house and a blue car";
let result = text.replace(/blue/gi, "red"); 

console.log(result); 
//Result: Mr red has a red house and a red car 
```

# Split

The `split()` method divides a string into a list of substrings and returns them as an array.
* using the `split()` method
* using the template literal (introduced in ES6)

The `split()` method takes in:

* **separator (optional)** - The pattern (string or regular expression) describing where each split should occur.
* **limit (optional)** - A non-negative integer limiting the number of pieces to split the given string into.

```javascript
console.log("ABCDEF".split("")); // [ 'A', 'B', 'C', 'D', 'E', 'F' ]

const text = "Java is awesome. Java is fun.";

let pattern = ".";
let newText = text.split(pattern);
console.log(newText); // [ 'Java is awesome', ' Java is fun', '' ]

let pattern1 = ".";
// only split string to maximum to parts
let newText1 = text.split(pattern1, 2);
console.log(newText1); // [ 'Java is awesome', ' Java is fun' ]

const text2 = "JavaScript ;  Python ;C;C++";
let pattern2 = ";";
let newText2 = text2.split(pattern2);
console.log(newText2); // [ 'JavaScript ', '  Python ', 'C', 'C++' ]

// using RegEx
let pattern3 = /\s*(?:;|$)\s*/;
let newText3 = text2.split(pattern3);
console.log(newText3); // [ 'JavaScript', 'Python', 'C', 'C++' ]

//Output
[ 'A', 'B', 'C', 'D', 'E', 'F' ]
[ 'Java is awesome', ' Java is fun', '' ]
[ 'Java is awesome', ' Java is fun' ]
[ 'JavaScript ', '  Python ', 'C', 'C++' ]
[ 'JavaScript', 'Python', 'C', 'C++' ]
```

# Substring

The `string.substring()` is an inbuilt function in JavaScript that is used to return the part of the given string from the start index to the end index. Indexing start from zero `(0)`. 

Syntax: 

`string.substring(StartIndex, EndIndex)`

### Syntax:

* using `str.substr(start , length)`
* using the `substr()` method
* using the template `(``)` literal (introduced in [ES6](../es6-concepts/template-literals.md))

The `substr()` method takes in:

* **parameters**: Here the StartIndex and EndIndex describe the part of the string to be taken as a substring. Here, the EndIndex is optional. 
* **return value**: It returns a new string that is part of the given string. JavaScript code to show the working of `string.substring()` function: 

```javascript
//Example 1:
// JavaScript to illustrate substr() method

const str = "GeeksforGeeks";
const result = str.substring(8);
console.log(result);



//Output
for

```

```javascript

//Example 2: 
// Taking a string as letiable
let string = "geeksforgeeks";
a = string.substring(-1)
b = string.substring(2.5)
c = string.substring(2.9)

// Printing new string which are
// the part of the given string
console.log(a);
console.log(b);
console.log(c);


//Output
geeksforgeeks
eksforgeeks
eksforgeeks
```
