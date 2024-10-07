# 第九章·对象

In javascript the objects are **mutable** because we change the values pointed by the reference object, instead, when we change a primitive value we are changing its reference which now is pointing to the new value and so primitive are **immutable**. The primitive types of JavaScript are `true`, `false`, `numbers`, `strings`, `null` and `undefined`. Every other value is an `object`. Objects contain `propertyName`: `propertyValue` pairs. There are three ways to create an `object` in JavaScript:

1.  **literal**

    ```javascript
    let object = {};
    // Yes, simply a pair of curly braces!
    ```

    > _**Note:**_ this is the **recommended** way.
2.  **object-oriented**

    ```javascript
    let object = new Object();
    ```

    > _**Note:**_ it's almost like Java.
3.  **using `object.create`**

    ```javascript
    let object = Object.create(proto[, propertiesObject]);
    ```

    > _**Note:**_ It creates a new object with the specified prototype object and properties.

In this chapter, we will explore following topics:
* [Delete](./delete.md)
* [Enumeration](./enumeration.md)
* [Mutable](./mutable.md)
* [Properties](./properties.md)
* [Prototype](./prototype.md)
* [Reference](./reference.md)


# Delete Operator

The `delete` operator can be used to **remove a property** from an object. When a property is deleted, it is removed from the object and cannot be accessed or enumerated (i.e., it does not show up in a for-in loop).

Here's the syntax for using `delete`:

```javascript
delete object.property;
```

For example:

```javascript
let adult = { age: 26 },
  child = Object.create(adult);
  
child.age = 8;

delete child.age;

/* Remove age property from child, revealing the age of the prototype, because then it is not overridden. */

let prototypeAge = child.age;
// 26, because child does not have its own age property.
```

{% hint style="warning" %}
The `delete` operator only works on own properties of an object, and not on inherited properties. It also does not work on properties that have the `configurable` attribute set to `false`.
{% endhint %}

The `delete` operator does not modify the object's prototype chain. It simply removes the specified property from the object and also it does not actually destroy the object or its properties. It simply makes the properties inaccessible. If you need to destroy an object and release its memory, you can set the object to `null` or use a garbage collector to reclaim the memory.

# Enumeration

_Enumeration_ refers to the process of iterating over the properties of an object and performing a certain action for each property. There are several ways to enumerate the properties of an object in JavaScript.

One way to enumerate the properties of an object is to use the `for-in` loop. The `for-in` loop iterates over the enumerable properties of an object in an arbitrary order, and for each property it executes a given block of code.

The `for in` statement can loop over all of the property names in an object. The enumeration will include functions and prototype properties.

```javascript
let fruit = {
    apple: 2,
    orange: 5,
    pear: 1,
  },
  sentence = "I have ",
  quantity;
for (kind in fruit) {
  quantity = fruit[kind];
  sentence += quantity + " " + kind + (quantity === 1 ? "" : "s") + ", ";
}
// The following line removes the trailing comma.
sentence = sentence.substr(0, sentence.length - 2) + ".";
// I have 2 apples, 5 oranges, 1 pear.
```

Another way to enumerate the properties of an object is to use the `Object.keys()` method, which returns an array of the object's own enumerable property names.

For example:

```typescript
let object = {
  foo: 'bar',
  baz: 'qux'
};

let properties = Object.keys(object);
properties.forEach(function(property) {
  console.log(property + ': ' + object[property]);
});

// foo: bar
// baz: qux
```

# Mutable

The difference between objects and primitive values is that we can **change objects**, whereas primitive values are **immutable**.

For example:

```javascript
let myPrimitive = "first value";
myPrimitive = "another value";
// myPrimitive now points to another string.
let myObject = { key: "first value" };
myObject.key = "another value";
// myObject points to the same object.
```

You can **add**, **modify**, or **delete** properties of an object using the dot notation or the square bracket notation.

```javascript
let object = {};
object.foo = 'bar'; // Add property 'foo'
object['baz'] = 'qux'; // Add property 'baz'
object.foo = 'quux'; // Modify property 'foo'
delete object.baz; // Delete property 'baz'
```

{% hint style="warning" %}
Primitive values (such as numbers and strings) are immutable, while objects (such as arrays and objects) are mutable.
{% endhint %}

# Properties

Object's property is a `propertyName`: `propertyValue` pair, where **property name can be only a string**. If it's not a string, it gets casted into a string. You can specify properties **when creating** an object **or later**. There may be zero or more properties separated by commas.

```javascript
let language = {
  name: "JavaScript",
  isSupportedByBrowsers: true,
  createdIn: 1995,
  author: {
    firstName: "Brendan",
    lastName: "Eich",
  },
  // Yes, objects can be nested!
  getAuthorFullName: function () {
    return this.author.firstName + " " + this.author.lastName;
  },
  // Yes, functions can be values too!
};
```

The following code demonstrates how to **get** a property's value.

```javascript
let variable = language.name;
// variable now contains "JavaScript" string.
variable = language["name"];
// The lines above do the same thing. The difference is that the second one lets you use litteraly any string as a property name, but it's less readable.
variable = language.newProperty;
// variable is now undefined, because we have not assigned this property yet.
```

The following example shows how to **add** a new property **or change** an existing one.

```javascript
language.newProperty = "new value";
// Now the object has a new property. If the property already exists, its value will be replaced.
language["newProperty"] = "changed value";
// Once again, you can access properties both ways. The first one (dot notation) is recommended.
```

# Prototype

Every object is linked to a prototype object from which it inherits properties. The objects created from object literals (`{}`) are automatically linked to `Object.prototype`, which is an object that comes standard with JavaScript.

When a JavaScript interpreter (a module in your browser) tries to find a property, that you want to retrieve, like in the following code:

```javascript
let adult = { age: 26 },
  retrievedProperty = adult.age;
// The line above
```

First, the interpreter looks through every property the object itself has. For example, `adult` has only one own property—`age`. However, it also has several properties inherited from `Object.prototype`.

```javascript
let stringRepresentation = adult.toString();
// the variable has value of '[object Object]'
```

The `toString` is an `Object.prototype`'s property, which was inherited. It has a value of a function, which returns a string representation of the object. If you want it to return a more meaningful representation, then you can override it. Simply add a new property to the adult object.

```javascript
adult.toString = function () {
  return "I'm " + this.age;
};
```

If you call the `toString` function now, the interpreter will find the new property in the object itself and stop.

Thus the interpreter retrieves the first property it will find on the way from the object itself and further through its prototype.

To set your own object as a prototype instead of the default `Object.prototype`, you can invoke `Object.create` as follows:

```javascript
let child = Object.create(adult);

/* This way of creating objects lets us easily replace the default Object.prototype with the one we want. In this case, the child's prototype is the adult object. */

child.age = 8;

/* Previously, child didn't have its own age property, and the interpreter had to look further to the child's prototype to find it.
 Now, when we set the child's own age, the interpreter will not go further.
 Note: adult's age is still 26. */

let stringRepresentation = child.toString();

// The value is "I'm 8".
/* Note: we have not overridden the child's toString property, thus the adult's method will be invoked. If adult did not have toString property, then Object.prototype's toString method would be invoked, and we would get "[object Object]" instead of "I'm 8" */
```

The `child`'s prototype is `adult`, whose prototype is `Object.prototype`. This sequence of prototypes is called a  **prototype chain**.

# Reference

Objects are **never copied**. They are passed around by reference. An object's reference is a value that refers to an object. When you create an object using the `new` operator or object literal syntax, JavaScript creates an object and assigns a reference to it.

Here's an example of creating an object using the object literal syntax:

```javascript
var object = {
  foo: 'bar'
};
```

Here's an example of creating an object using the `new` operator:

```javascript
var object = new Object();
object.foo = 'bar';
```

When you assign an object reference to a variable, the variable simply holds a reference to the object, not the object itself. This means that if you assign the object reference to another variable, both variables will point to the same object.

For example:

```javascript
var object1 = {
  foo: 'bar'
};

var object2 = object1;

console.log(object1 === object2); // Output: true
```

In the example above, both `object1` and `object2` are variables that hold references to the same object. The `===` operator is used to compare the references, not the objects themselves, and it returns `true` because both variables hold references to the same object.

{% hint style="info" %}
You can use the `Object.assign()` method to create a new object that is a copy of an existing object.&#x20;
{% endhint %}

Following is an example of creating an object by reference.

```javascript
// Imagine I had a pizza
let myPizza = { slices: 5 };
// And I shared it with You
let yourPizza = myPizza;
// I eat another slice
myPizza.slices = myPizza.slices - 1;
let numberOfSlicesLeft = yourPizza.slices;
// Now We have 4 slices because myPizza and yourPizza
// reference to the same pizza object.
let a = {},
  b = {},
  c = {};
// a, b, and c each refer to a
// different empty object
a = b = c = {};
// a, b, and c all refer to
// the same empty object
```
