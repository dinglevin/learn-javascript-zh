# 第六章·数组

Arrays are a fundamental part of programming. An array is a list of data. We can store a lot of data in one variable, which makes our code more readable and easier to understand. It also makes it much easier to perform functions on related data.

The data in arrays are called **elements**.

Here is a simple array:

```javascript
// 1, 1, 2, 3, 5, and 8 are the elements in this array
let numbers = [1, 1, 2, 3, 5, 8];
```

Arrays can be created easily using array literals or with a `new` keyword.&#x20;

```javascript
const cars = ["Saab", "Volvo", "BMW"]; // using array literals
const cars = new Array("Saab", "Volvo", "BMW"); // using the new keyword
```

An index number is used to access the values of an array.  The index of the first element in an array is always `0` as array indexes start with `0`. The index number can also be used to change the elements of an array.

```javascript
const cars = ["Saab", "Volvo", "BMW"];
console.log(cars[0]); 
// Result: Saab

cars[0] = "Opel"; // changing the first element of an array
console.log(cars);
// Result: ['Opel', 'Volvo', 'BMW']
```

{% hint style="warning" %}
Arrays are a special type of object.  One can have [objects](../objects/) in an array.
{% endhint %}

&#x20;The `length` property of an array returns the count of numbers elements.  Methods supported by Arrays are shown below:

| Name              | Description                                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `at()`            | Returns element at the specified index or `undefined`                                                                                             |
| `concat()`        | Returns two or more combined arrays                                                                                                               |
| `every()`         | Returns `true` if `callback` returns `true` for every item in the array                                                                           |
| `filter()`        | Returns a new array containing the items for which `callback` returned `true`                                                                     |
| `find()`          | Returns the first item for which `callback` returned `true`                                                                                       |
| `findIndex()`     | Returns the index of the first item for which `callback` returned `true`                                                                          |
| `findLast()`      | Returns the last item for which `callback` returned `true`                                                                                        |
| `findLastIndex()` | Returns the index of the last item for which `callback` returned `true`                                                                           |
| `flat()`          | Returns a new array with all sub-array elements concatenated into it recursively up to the specified depth                                        |
| `flatMap()`       | Runs `map()` followed by `flat()` of depth 1                                                                                                      |
| `forEach()`       | Executes a callback in each element of an array and returns undefined                                                                             |
| `indexOf()`       | Returns the index of the first match of the search element                                                                                        |
| `join()`          | Joins all elements in an array into a string                                                                                                      |
| `lastIndexOf()`   | Returns the index of the last match of the search element                                                                                         |
| `map()`           | Returns a new array with a return value from executing `callback` on every array item.                                                            |
| `pop()`           | Removes the last element of an array and returns that element                                                                                     |
| `push()`          | Adds one or more elements at the end of the array and returns the length                                                                          |
| `reduce()`        | Uses `callback(accumulator, currentValue, currentIndex, array)` for reducing purpose and returns the final value returned by `callback` function  |
| `reduceRight()`   | Works similarly like `reduce()` but starts with the last element                                                                                   |
| `reverse()`       | Transposes the elements of an array and returns a reference to an array                                                                           |
| `shift()`         | Removes the first element of an array and returns that element                                                                                    |
| `slice()`         | Extracts the section of an array and returns the new array                                                                                        |
| `some()`          | Returns `true` if `callback` returns `true` for at least one item in the array                                                                    |
| `sort()`          | Sorts the elements of an array in place, and returns a reference to the array                                                                     |
| `splice()`        | Removes elements from an array and (optionally) replaces them, and returns the array                                                              |
| `unshift()`       | Adds one or more elements at the front of an array and returns the length                                                                         |

In this chapter, we will explore following topics:
* [For-Each](./for-each.md)
* [Indices](./indices.md)
* [Join](./join.md)
* [Length](./length.md)
* [Map](./map.md)
* [Pop](./pop.md)
* [Push](./push.md)
* [Reverse](./reverse.md)
* [Shift](./shift.md)
* [Slice](./slice.md)
* [Sort](./sort.md)
* [Spread](./spread.md)
* [Unshift](./unshift.md)

# For Each

The `forEach` method executes a provided function once for each array element. Here's the syntax for using `forEach`:

```javascript
array.forEach(function(element, index, array) {
  // element: current element being processed in the array
  // index: index of the current element being processed in the array
  // array: the array forEach was called upon
});
```


For example, let's say you have an array of numbers and you want to print the double of each number to the console. You could do this using `forEach` like this:

```typescript
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number) {
  console.log(number * 2);
});
```

You can also use the arrow function syntax to define the function passed to `forEach`:

```typescript
numbers.forEach((number) => {
  console.log(number * 2);
});
```

or

```typescript
numbers.forEach(number => console.log(number * 2));
```

The `forEach` method does not modify the original array. It simply iterates over the elements of the array and executes the provided function for each element.

{% hint style="warning" %}
The `forEach()` method is not executed for the empty statement.
{% endhint %}

# Indices

So you have your array of data elements, but what if you want to access a specific element? That is where indices come in. An **index** refers to a spot in the array. Indices logically progress one by one, but it should be noted that the first index in an array is `0`, as it is in most languages. Brackets `[]` are used to signify you are referring to an index of an array.

```javascript
// This is an array of strings
let fruits = ["apple", "banana", "pineapple", "strawberry"];

// We set the variable banana to the value of the second element of
// the fruits array. Remember that indices start at 0, so 1 is the
// second element. Result: banana = "banana"
let banana = fruits[1];
```

You can also use an array index to set the value of an element in an array:

```javascript
let array = ['a', 'b', 'c', 'd', 'e'];
//  indices:  0    1    2    3    4
array[4] = 'f';
console.log(array); // Result: ['a', 'b', 'c', 'd', 'f']
```

Note that if you try to access or set an element using an index that is outside the bounds of the array (i.e., an index that is less than `0` or greater than or equal to the length of the [array](./README.md)), you will get an `undefined` value.

```javascript
console.log(array[5]); // Output: undefined
array[5] = 'g';
console.log(array); // Result: ['a', 'b', 'c', 'd', 'f', undefined, 'g']
```

# Join

The `join` method, makes an array turn into a string and joins it all together. It does not change the original array. Here's the syntax for using `join`:

```c
array.join([separator]);
```

The `separator` argument is optional and specifies the character to be used to separate the elements in the resulting string. If omitted, the array elements are separated with a comma (`,`).

For example:

```javascript
let array = ["one", "two", "three", "four"]; 

console.log(array.join(" ")); 

// Result: one two three four
```

{% hint style="warning" %}
Any separator can be specified but the default one is a comma `(,)`.
{% endhint %}

In the above example, a space is used as a separator. You can also use `join` to convert an array-like object (such as an arguments object or a NodeList object) to a string by first converting it to an array using the `Array.prototype.slice()` method:

```javascript
function printArguments() {
  console.log(Array.prototype.slice.call(arguments).join(', '));
}

printArguments('a', 'b', 'c'); // Result: "a, b, c"
```

# Length

Arrays have a property called `length`, and it's pretty much exactly as it sounds, it's the length of the array.

```javascript
let array = [1, 2, 3];

let l = array.length;

// Result: l = 3
```

The length property also sets the number of elements in an array. For example.

```javascript
let fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.length = 2;

console.log(fruits);
// Result: ['Banana', 'Orange']
```

You can also use the `length` property to get the last element of an array by using it as an index. For example:

```c
console.log(fruits[fruits.length - 1]); // Result: Orange
```

You can also use the `length` property to add elements to the end of an array. For example:

```c
fruits[fruits.length] = "Pineapple";
console.log(fruits); // Result: ['Banana', 'Orange', 'Pineapple']
```

{% hint style="info" %}
The `length` property is automatically updated when elements are added or removed from the array.
{% endhint %}

It's also worth noting that the `length` property is not a method, so you don't need to use parentheses when accessing it. It's simply a property of the array object that you can access like any other object property.

# Map

The `Array.prototype.map()` method iterates over an array and modifies its elements using a callback function. The callback function will then be applied to each element of the array.

Here's the syntax for using `map`.

```javascript
let newArray = oldArray.map(function(element, index, array) {
  // element: current element being processed in the array
  // index: index of the current element being processed in the array
  // array: the array map was called upon
  // Return element to be added to newArray
});
```

For example, let's say you have an array of numbers and you want to create a new array that doubles the values of the numbers in the original array. You could do this using `map` like this.

```javascript
const numbers = [2, 4, 6, 8];

const doubledNumbers = numbers.map(number => number * 2);

console.log(doubledNumbers);

// Result: [4, 8, 12, 16]
```

You can also use the arrow function syntax to define the function passed to `map`.

<pre class="language-typescript"><code class="lang-typescript"><strong>let doubledNumbers = numbers.map((number) => {
</strong>  return number * 2;
});
</code></pre>

or

```typescript
let doubledNumbers = numbers.map(number => number * 2);
```

{% hint style="info" %}
The `map()` method doesn't execute function for empty elements and doesn't change the original array.
{% endhint %}

# Pop

The `pop` method removes the last element from an array and returns that element. This method changes the length of the array.

Here's the syntax for using `pop`:

```c
array.pop();
```

For example:

```javascript
let arr = ["one", "two", "three", "four", "five"]; 
arr.pop(); 

console.log(arr); 

// Result: ['one', 'two', 'three', 'four']
```

You can also use the `pop` method in conjunction with a loop to remove all elements from an array. Here's an example of how you might do this:

```c
while (array.length > 0) {
  array.pop();
}

console.log(array); // Result: []
```

{% hint style="warning" %}
The `pop` method only works on arrays, and not on other objects that are similar to arrays such as arguments objects or NodeList objects. If you need to pop elements from one of these types of objects, you will need to convert it to an array first using the `Array.prototype.slice()` method.

{% endhint %}

# Push

One can push certain items to an array making the last index the newly added item. It changes the length of an array and returns a new length.

Here's the syntax for using `push`:

```c
array.push(element1[, ...[, elementN]]);
```

The `element1, ..., elementN` arguments represent the elements to be added to the end of the array.

For example:

```javascript
let array = [1, 2, 3]; 
array.push(4); 

console.log(array); 

// Result: array = [1, 2, 3, 4]
```

You can also use `push` to add elements to the end of an array-like object (such as an arguments object or a NodeList object) by first converting it to an array using the `Array.prototype.slice()` method:

```javascript
function printArguments() {
  let args = Array.prototype.slice.call(arguments);
  args.push('d', 'e', 'f');
  console.log(args);
}

printArguments('a', 'b', 'c'); // Result: ["a", "b", "c", "d", "e", "f"]
```

> **Note**: The `push` method modifies the original array. It does not create a new array.

# Reverse

The `reverse` method can be used on any type of array, including arrays of strings, arrays of numbers, and arrays of objects. For example.

```javascript
let users = [{
  name: "John Smith",
  age: 30
}, {
  name: "Jane Doe",
  age: 25
}];

users.reverse();

console.log(users);

// RESULT: 
[{
  name: "Jane Doe",
  age: 25
}, {
  name: "John Smith",
  age: 30
}];
```

The `reverse` method transposes the elements of the calling array object in place, mutating the array, and returning a reference to the array.
Here is an example of using `reverse` of an array:

```javascript
const numbers = [1, 2, 3];
const newLength = numbers.reverse();
console.log(numbers); // [3, 2, 1]
```

# Shift

The `shift` method deletes the first index of that array and moves all indexes to the left. It changes the original array. Here's the syntax for using `shift`:

```c
array.shift();
```

For example:&#x20;

```javascript
let array = [1, 2, 3]; 
array.shift(); 

// Result: array = [2,3]
```

You can also use the `shift` method in conjunction with a loop to remove all elements from an array. Here's an example of how you might do this:

```c
while (array.length > 0) {
  array.shift();
}

console.log(array); // Result: []
```

{% hint style="warning" %}
The `shift` method only works on arrays, and not on other objects that are similar to arrays such as arguments objects or NodeList objects. If you need to shift elements from one of these types of objects, you will need to convert it to an array first using the `Array.prototype.slice()` method.
{% endhint %}

# Slice

The `slice` method accepts two parameters begin and end.
* **begin**: This parameter defines the starting index from where the portion is to be extracted. 
  If this argument is missing then the method takes begin as `0` as it is the default start value.
* **end**: This parameter is the index up to which the portion is to be extracted (excluding the end index). 
  If this argument is not defined then the array till the end is extracted as it is the default end value If the end value is greater than the length of the array, then the end value changes to the length of the array.

```javascript
function func() {
	//Original Array
	let arr = [23, 56, 87, 32, 75, 13];
	//Extracted array
	let new_arr = arr.slice();
	console.log(arr);
	console.log(new_arr);
}
func();


// RESULT: 
[23,56,87,32,75,13]
[23,56,87,32,75,13]
```

The `slice()` method copies object references to the new array (example, a nested array). So, if the referenced object is modified, the changes are visible in the returned new array.

```javascript
let human = {
  name: "David",
  age: 23,
};

let arr = [human, "Nepal", "Manager"];
let new_arr = arr.slice();

// original object
console.log(arr[0]); // { name: 'David', age: 23 }

// making changes to the object in new array
new_arr[0].name = "Levy";

// changes are reflected
console.log(arr[0]); // { name: 'Levy', age: 23 }
```

# Sort

The `sort` method sorts the items of an array in a specific order (ascending or descending). By default, the `sort` method sorts the elements as strings and arranges them in ascending order based on their UTF-16 code unit values.

Here's the syntax for using `sort`:

```c
array.sort([compareFunction]);
```

The `compareFunction` argument is optional and specifies a function that defines the sort order. If omitted, the elements are sorted in ascending order according to their string representation.

For example:

```javascript
let city = ["California", "Barcelona", "Paris", "Kathmandu"];
let sortedCity = city.sort(); 

console.log(sortedCity);

// Result: ['Barcelona', 'California', 'Kathmandu', 'Paris']

```

{% hint style="info" %}
Numbers can be sorted incorrectly when they are sorted. For example, "35" is bigger than "100", because "3" is bigger than "1".
{% endhint %}

To fix the sorting issue in numbers, compare functions are used. Compare functions defines sort orders and return a **negative**, **zero**, or **positive** value based on arguments, like this:

* A negative value if `a` should be sorted before `b`
* A positive value if `a` should be sorted after `b`
* `0` if `a` and `b` are equal and their order doesn't matter

```javascript
const points = [40, 100, 1, 5, 25, 10];
points.sort((a, b) => {return a-b});

// Result: [1, 5, 10, 25, 40, 100]
```

{% hint style="warning" %}
The `sort()` method overrides the original array.
{% endhint %}

# Spread

An array or object can be quickly copied into another array or object by using the Spread Operator `(...)`. It allows an iterable such as an array to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

Here are some  examples of it:

```javascript
let arr = [1, 2, 3, 4, 5]; 

console.log(...arr); 
// Result: 1 2 3 4 5

let arr1;
arr1 = [...arr]; //copies the arr into arr1 

console.log(arr1);    //Result: [1, 2, 3, 4, 5]

arr1 = [6,7];
arr = [...arr,...arr1];

console.log(arr);   //Result: [1, 2, 3, 4, 5, 6, 7]

```

{% hint style="warning" %}
The spread operator only works in modern browsers that support the feature. If you need to support older browsers, you will need to use a transpiler like Babel to convert the spread operator syntax to equivalent ES5 code.
{% endhint %}

# Unshift

The `unshift` method adds new elements sequentially to the start, or front of the array. It modifies the original array and returns the new length of the array. For example.

```javascript
let array = [0, 5, 10];
array.unshift(-5);  // 4

// RESULT: array = [-5 , 0, 5, 10];
```

{% hint style="warning" %}
The `unshift()` method overwrites the original array.
{% endhint %}

The `unshift` method takes one or more arguments, which represent the elements to be added to the beginning of the array. It adds the elements in the order they are provided, so the first element will be the first element of the array.

Here is an example of using `unshift` to add multiple elements to an array:

```javascript
const numbers = [1, 2, 3];
const newLength = numbers.unshift(-1, 0);
console.log(numbers); // [-1, 0, 1, 2, 3]
console.log(newLength); // 5
```
