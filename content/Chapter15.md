# 第十五章·类

Classes are templates for creating an object. It encapsulates data with code to work on with data. For example if we want to make a family tree of birds, we can make a bird class and every bird object we make will have the methods and data from the bird class. 

 The keyword `class` is used to create a class.  And a specific method called `constructor` is used for creating and initializing an object created with a `class`. An example of car class is shown below.

```javascript
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}

let myCar = new Car("Toyota", 2021);
console.log(myCar.age()) // 1
```

{% hint style="info" %}
Class must be defined before its usage.
{% endhint %}

In the class body, methods or constructors are defined and executed in `strict mode`. Syntax not adhering to the strict mode results in error.&#x20;

Every time we create an object from a class we’re creating an **instance** of that class, for example the `myCar` variable above us with the `new` keyword is an instance. Instances are *independant* meaning it doesn’t affect any other instance. This is why classes are thought to be templates for objects. Since once you make that instance object it'll have the same methods as the original class.


In this chapter, we will explore following topics:
* [Access Modifiers](./access-modifiers.md)
* [Composition](./composition.md)
* [Inheritance](./inheritance.md)
* [Static](./static.md)

# Access Modifiers

`public`, `private`, and `protected` are the three access modifiers used in class to control its access from the outside. By default, all members (properties, fields, methods, or functions) are publicly accessible from outside the class.

```javascript
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let myCar = new Car("Toyota");
console.log(Car.hello(myCar)); // Hello Toyota
```

`private`  members can access only internally within the class and cannot be accessible from outside.  Private should start with `#`.

```javascript
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
  #present(carname) {
    return 'I have a ' + this.carname;
  }
}
let myCar = new Car("Toyota");
console.log(myCar.#present("Camry")); // Error
console.log(Car.hello(myCar)); // Hello Toyota
```

`protected` fields are accessible only from inside the class and those extending it. These are useful for the internal interface as the inheriting class also gains access to the parent class.  Protected fields with `_` .

```javascript
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  _present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this._present() + ', it is a ' + this.model;
  }
}
let myCar = new Model("Toyota", "Camry");
console.log(myCar.show()) // I have a Toyota, it is a Camry
```

# Composition

Composition is useful for creating "has-a" relationships that ensure loose coupling and flexibility. If we imagine that our class is a wall, the classes that make it up via composition are like bricks - smaller and more manageable components.

## Benefits of composition

  + Reusability - Components can be reused throughout different parts of the application.

  + Maintainability - Changes in one component have minimal impact on others.

  + Flexibility - It's easier to change the application's behavior by changing different components rather than larger and more complex structures.

  + Single responsibility - It keeps each class encapsulated and focused on a single task, adhering to the single responsibility principle.

```javascript
class Book {
  constructor(title, author) {
    this.title = title;
    this.author = author;
  }
}

class Library {
  constructor() {
    this.books = [];
  }
  
  add(book) {
    this.books.push(book);
    return `${book.title} was added to the library.`;
  }
}

let myBook = new Book("The Great Gatsby", "F. Scott Fitzgerald");
let myLibrary = new Library();

console.log(myLibrary.add(myBook)); // The Great Gatsby was added to the library.
```

In the example above, instances of the `Book` class are used to create the larger `Library` class. Composition is used to create a "has-a" relationship between the two classes (a library has books inside it), which ensures loose coupling. Changes to the `Book` class won't be reflected on the `Library` class,  and vice versa.

## Composition vs Inheritance

While inheritance creates an "is-a" relationship (e.g., a `Car` is a `Vehicle`), composition creates a "has-a" relationship (e.g., a `Car` has an `Engine`). Here are some pros and cons for using both:

| **Feature**          | **Inheritance**                                                                 | **Composition**                                                              |
|----------------------|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| **Pros**             | - Simple and intuitive for modeling class relationships <br> - Code reuse through base classes | - Loose coupling <br> - High flexibility <br> - Easier maintenance           |
| **Cons**             | - Tight coupling <br> - Less flexibility <br> - Deep inheritance hierarchies     | - More complex to set up and understand <br> - Fewer classes but more objects |

# Inheritance

The inheritance is useful for code reusability purposes as it extends existing properties and methods of a class. The `extends` keyword is used to create a class inheritance. &#x20;

```javascript
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

let myCar = new Model("Toyota", "Camry");
console.log(myCar.show()); // I have a Camry, it is a Toyota.
```

{% hint style="info" %}
The prototype of the parent class must be an `Object` or `null`.&#x20;
{% endhint %}

The `super` method is used inside a constructor and refers to the parent class. With this, one can access the parent class properties and methods. In  the example above we use `super(brand)` in the Model subclass so it can get that `Car` superclasses properties.

{% hint style="info" %}
Super classes are the main classes used while subclasses are classes that are extended from superclasses.
{% endhint %}

# Static

The `static` keyword defines the static methods or properties for a class.  These methods and properties are called in the class itself.&#x20;

```javascript
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let myCar = new Car("Toyota");

console.log(myCar.hello()); // This will throw an error
console.log(Car.hello(myCar));
// Result: Hello Toyota
```

{% hint style="info" %}
One can access the static method or property of another static method of the same class using `this` keyword.
{% endhint %}
