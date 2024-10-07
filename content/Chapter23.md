# 第二十三章·设计模式

Design patterns are object oriented solutions that you can  implement to solve common programming problems that may occur during the development process. Design patterns are not the same as algorithms, they are a coding concept that you can use to resolve specific kinds of issues. 

There are various design patterns that are not unique to any one language. These fundamental concepts can be applied across a wide variety of programming languages. Today, we will learn about each design pattern and how to implement them using JavaScript. Design patterns can be classified into one of three categories.


* [Creational Patterns](./creational-patterns.md)
* [Structural Patterns](./structural-patterns.md)
* [Behavioral Patterns](./behavioral-patterns.md)

# Creational Design Patterns

Creational design patterns focus on object creation mechanisms

## 1. Factory Method

A factory function is just a function that creates an object and returns it. It is a creational design pattern that allows you to create objects without specifying the exact class or constructor to be used. It centralizes object creation logic, allowing for flexibility in creating different types of objects. Lets say you have a website and you want to create a method that will allow you to easily create html objects and add it to the DOM. A factory is the perfect solution for this and here is how we can implement it 

### 1.1. Components of the Factory Method

*Creator*: This is the method implemented in the Factory that creates new products. 

*Abstract Product*: An interface for the product being created.

*Concrete Product*: This is the actual object being created. 

### 1.2. Benefits of the Factory Method

**Abstraction of Object Creation**

It removes the complexity of creating an object, allowing the client code to just focus on the created objects. 

**Flexibility and Customization**

Factories enable customization of the object creation process, allowing for variations in the created objects

**Encapsulation of Creation Logic**

The creation logic is encapsulated within the factory, making it easier to modify or extend the creation process without affecting client code

**Complex Object Creation**

Factories are useful when the creation of objects is complex, involves multiple steps,  or requires certain conditions to be met.

### 1.3. Example

```javascript
    function elementFactory(type, text, color){
        const newElement = document.createElement(type)
        newElement.innerText = text 
        newElement.style.color = color 
        document.body.append(newElement)
        
        
    function setText(newText) {
         newElement.innerText = newText;
    }
        
    function setColor(newColor) { 
        newElement.innerText = newColor; 
    }
        
    return {
        newElement, 
        setText,
        setColor,
        }

    }

const h1Tag = elementFactory('h1','Initial Text','Blue'); 

h1Tag.setText('Hello world');

h1Tag.setColor('Red');
```

## 2. Abstract Factory Method

Abstract factories are another creational design pattern. Its main goal is to provide an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern ensures that the created objects are compatible and work together. 

### 2.1. The 4 Components of an Abstract Factory

*Abstract Factories*

This defines the interface for creating the abstract products, which are related families of objects (e.g. UI components).The abstract factory declares creation methods for each type of product in the family. 

*Concreate Factories*

These are classes that implement the abstract factory interface, providing specific implementations for creating the concrete products. Each concrete factory creates a family of related products (e.g. UI factory might create a button or checkbox).

*Abstract Products*

These are the interfaces or base classes for the products that the abstract factory creates. Each product type in the family has its own abstract product definition (e.g., Button, Checkbox).

*Concrete Products*

These are the actual implementations of the abstract products. Each concrete factory creates its own set of concrete products.Concrete products implement the abstract product interfaces defined for their family (e.g., HTMLButton, WindowsButton).

### 2.2. Benefits of Abstract Factories

**Consistency**

It ensures that created objects are compatible and follow a consistent theme or style.

**Isolation of Responsibilities** 

It isolates the creation of objects from the client code, promoting a clean separation of concerns.

**Flexibility and Scalability**

It allows for easy addition of new product families without modifying existing client code.

### 2.3. Example 

```javascript 
 // Abstract Factory: UIFactory
class UIFactory {
    createButton() {
        throw new Error('createButton method must be overridden');
    }

    createCheckbox() {
        throw new Error('createCheckbox method must be overridden');
    }
}

// Concrete Factory: WindowsUIFactory
class WindowsUIFactory extends UIFactory {
    createButton() {
        return new WindowsButton();
    }

    createCheckbox() {
        return new WindowsCheckbox();
    }
}

// Concrete Factory: MacUIFactory
class MacUIFactory extends UIFactory {
    createButton() {
        return new MacButton();
    }

    createCheckbox() {
        return new MacCheckbox();
    }
}

// Abstract Product: Button
class Button {
    render() {
        throw new Error('render method must be overridden');
    }
}

// Concrete Product: WindowsButton
class WindowsButton extends Button {
    render() {
        console.log('Rendering a Windows button');
    }
}

// Concrete Product: MacButton
class MacButton extends Button {
    render() {
        console.log('Rendering a Mac button');
    }
}

// Abstract Product: Checkbox
class Checkbox {
    render() {
        throw new Error('render method must be overridden');
    }
}

// Concrete Product: WindowsCheckbox
class WindowsCheckbox extends Checkbox {
    render() {
        console.log('Rendering a Windows checkbox');
    }
}

// Concrete Product: MacCheckbox
class MacCheckbox extends Checkbox {
    render() {
        console.log('Rendering a Mac checkbox');
    }
}

// Usage
const windowsFactory = new WindowsUIFactory();
const macFactory = new MacUIFactory();

const windowsButton = windowsFactory.createButton();
windowsButton.render();  // Output: Rendering a Windows button

const macCheckbox = macFactory.createCheckbox();
macCheckbox.render();  // Output: Rendering a Mac checkbox
```

## 3. Builder 

The goal of a builder is to separate the construction of an object from its representation. What the builder pattern does is basically allow the client to construct a complex object by just passing in the type and content of the object only. The client does not have to worry about the construction details.

## 3.1. The 4 Components of a Builder

*Builder*

The builder usually contains a series of methods to build various parts of the object.

*Concrete Builder*

Implements methods from the builder interface to construct parts of the object 

*Director (Optional)* 

This is not always necessary but can help with constructing the final object using a specific construction process 

*Object* 

Representation of the final product. Contains parts that were constructed by the builder

## 3.2. Benefits of the Builder Pattern 

**Separation of Concerns**

The Builder pattern separates the construction of a complex object from its representation, allowing different implementations of builders to vary the internal representation.

**Flexible Object Creation**

It allows for the creation of different configurations of a complex object by using a common construction process. Builders can be tailored to create specific variations of the object

**Improved Readability**

Using a builder can improve code readability by clearly outlining the steps needed to construct an object. It's easy to understand what each step contributes to the final object.

**Parameterized Construction**

Builders allow you to construct an object by passing parameters to the construction steps, enabling fine-grained control over the object's creation and configuration.

**Reusability**

Builders can be reused to create multiple instances of the complex object with different configurations, promoting code reuse and minimizing duplication of construction logic.

## 3.3. Example 

```Javascript 
//Builder
class ComputerBuilder {
    buildCPU() {}
    buildRAM() {}
    buildStorage() {}
    getResult() {}
}

//Concrete Builders
class GamingComputerBuilder extends ComputerBuilder {
    // Implement specific steps to build a gaming computer
}

class OfficeComputerBuilder extends ComputerBuilder {
    // Implement specific steps to build an office computer
}

//Object class
class Computer {
    constructor() {
        this.parts = [];
    }

    addPart(part) {
        this.parts.push(part);
    }
}

// Director (Optional)
class ComputerAssembler {
    constructor(builder) {
        this.builder = builder;
    }

    assembleComputer() {
        this.builder.buildCPU();
        this.builder.buildRAM();
        this.builder.buildStorage();
        return this.builder.getResult();
    }
}
```

## 4. Singleton

A singleton is an object that can only be instantiated once. Singletons are useful when system wide actions need to be coordinated from a single central place. Singletons reduce the need for global variables which is particularly important in javascript because it limits namespace pollution.

## 4.1. Components of a Singleton

*Anonymous Function*

A singleton is implemented using a anonymous function

*getInstance Function*

This is a function which returns the unique instantiated object

*Constructor (Optional)* 

In javascript, a constructor is not necessary for implementing the singleton pattern but having a constructor is common because it allows you to configure the singleton and add initialization logic. 

## 4.2. Benefits of a Singleton 

**Reduce Global Variables**

Singletons can help reduce the number of global variables required in your program, promoting better code organization and maintainability. 

**Memory Efficient**

Because a Singleton ensures there is only ever one instance that exists at a time, memory is saved because you avoid having multiple instances of the same class.

**Global Point of Access**

Singletons provide a global point of access to the instance. This allows other parts of the program to access and use the same instance without needing to pass it around. 

**Resource Sharing**

Singletons are especially useful when it comes to tasks like managing shared resources. Singletons can be used to manage database connections, file handlers, and even thread pools, ensuring that these resources are shared efficiently across the application. 

## 4.3. Example 

```javascript
class Singleton {
  constructor() {
    const privateVariable = 'This is a private variable';

    function privateMethod() {
      console.log('This is a private method.');
    }

    return {
      publicMethod: function() {
        console.log('This is a public method.');
      },
      publicVariable: 'I am public'
    };
  }

  static getInstance() {
    if (!Singleton.instance) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }
}

const singletonInstance1 = Singleton.getInstance();
const singletonInstance2 = Singleton.getInstance();

console.log(singletonInstance1 === singletonInstance2); // Outputs: true
```

## 5. Prototype 

The prototype pattern is an alternative way to implement inheritance but the main difference is instead of inheriting properties from a class, objects inherit properties from a prototype object. The prototype pattern is also referred to as the properties pattern and Javascript has native support for prototypes. In Javascript, each object has a prototype (reference to another object). When you attempt to access a property that does not exist in the object itself Javascript will look for it in the object's prototype and continue up the prototype chain until it finds it or reaches the end of the chain. 

## 5.1. Components of the Prototype Pattern

*Prototype Object* 

Contains the properties and methods that all the new instances will inherit

*Client*

The client is responsible for creating new objects based on the prototype. The client can create new instances based on the prototype and modify their
properties accordingly. 

*Clone/Creation Mechanism*

 The mechanism used to create a new object based on the prototype. In Javascript this can be achieved using the `Object.create()` function. 

## 5.2. Benefits of the Prototype Pattern 

**Efficient Instance Creation**

Creating new instances of the Prototyope is more efficient that using traditional classes and constructors. Objects are created by cloning the prototype, which reduces the need for setting up classes and initialization logic. 

**Code Reusability**

The Prototype pattern allows you to define a set of default properties and methods in a prototype object. This allows multiple instances to share the same behaviour and structure without duplicating the code. This also reduces memory usage since each instance does not need to store duplicates of the prototypes properties. 

**Flexible Object Creation**

Objects created using the Prototype pattern can be easily customized by modifying their properties or adding new properties specific to the instance.

**Dynamic Runtime Changes** 

Changes made to the prototype object at runtime are reflected in all instances based on the prototype. This behavior allows for updates and modifications to the prototype, impacting all instances sharing the same prototype. 

## 5.3. Example 

```javascript 
const cameraPrototype = {
    model = 'default',
    make = 'default',
    shutter: function () {
        console.log(`The ${this.make} ${this.model} has taken a photo`);
    }
};

const camera1 = Object.create(cameraPrototype);
camera1.model = 'X-Pro 3';
camera1.make = 'Fujifilm';

const camera1 = Object.create(cameraPrototype);
camera1.model = 'R5';
camera1.make = 'Canon';
```

---

# Structural Design Patterns 

Focus on how classes and objects are composed to form larger structures

## 1. Adapter 

The Adapter is a structural design pattern that enables you to make make different interfaces with different methods work together without changing their code. The purpose of an Adapter is to make two incompatible interfaces work together seamlessly. 

## 1.1 Components of the Adapter 

*Target Interface/Class* 

This is the interface or class that the client will work with. It contains all the methods and properties that the client code will use. 

*Adaptee*

The Adaptee is the old interface/class that contains properties and methods that are incompatible with the new interface/class. 

*Adapter* 

The Adapter is what bridges the gap between the Adaptee and the Target interface/class 


## 1.2. Benefits of Adapters 

**Easy Integration**

Adapters create an easy way for new code or systems to interact with existing ones. By using Adapters, integrating new code becomes smoother and less error-prone. 

**Compatibility and Reusability**

Adapters promote code reuse and extends the usability of existing code by making older code compatible with newer code. 

**Gradual System Integration**

In situations where a new system needs to be implemented gradually, Adapters can serve as intermediaries, allowing new features to come in slowly while maintaining compatibility with the existing system. 

**Improved Testability**

Adapters facilitate easier testing by allowing mocking or stubbing of the adaptee during testing of the client code. This improves the testability of the client code and helps in wrtiting more comprehensible unit tests. 


## 1.3. Example 

```javascript 
// Adaptee: EU charging brick
class EUChargingBrick {
  chargeWithEUPlug() {
    console.log('Charging with EU plug');
  }
}

// Adaptee: US charging brick
class USChargingBrick {
  chargeWithUSPlug() {
    console.log('Charging with US plug');
  }
}

// Target: Common charging interface expected by the client
class ChargingInterface {
  charge() {
    console.log('Charging...');
  }
}

// Adapter for EU charging brick
class EUChargingAdapter extends ChargingInterface {
  constructor(euChargingBrick) {
    super();
    this.euChargingBrick = euChargingBrick;
  }

  charge() {
    this.euChargingBrick.chargeWithEUPlug();
  }
}

// Adapter for US charging brick
class USChargingAdapter extends ChargingInterface {
  constructor(usChargingBrick) {
    super();
    this.usChargingBrick = usChargingBrick;
  }

  charge() {
    this.usChargingBrick.chargeWithUSPlug();
  }
}

// Client
function chargeDevice(chargingInterface) {
  chargingInterface.charge();
}

// Usage
const euChargingBrick = new EUChargingBrick();
const euAdapter = new EUChargingAdapter(euChargingBrick);

const usChargingBrick = new USChargingBrick();
const usAdapter = new USChargingAdapter(usChargingBrick);

console.log('Charging with EU charging brick:');
chargeDevice(euAdapter);

console.log('Charging with US charging brick:');
chargeDevice(usAdapter);
```

## 2. Bridge 

The Bridge is a structural design pattern that is designed to split a very large class into two separate hierarchies which can be developed independendently. The two hierarchies are referred to as the Abstraction level and the Implementation level. Basically if you have a class that has multiple variants of some functionality, you can use a Bridge pattern to divide and organize the class into two easier to understand hierarchies. 

## 2.1. Components of the Bridge 

*Abstraction* 

This is the high-level interface or abstraction. It defines the abstract functionality that the clients will use. 

*Refined Abstraction* 

These are subclasses or extensions of the abstraction layer. These provide additional features or refinements. It extends the functionality defined by the abstraction. 

*Implementor* 

This is the interface that defines the implementation methods, It usually doesn't mirror the abstraction interface, but its a lower-level interface that the abstraction relies upon. 

*Concrete Implementor* 

Concrete classes that implement the implementor interface. Theses classes provide specific implementations of the methods defined by the implementor interface. 

## 2.2. Benefits of the Bridge Pattern

**Decouples Abstraction from Implementation**

The primary benefit of the Bridge pattern is it splits the abstraction layer from the implementation layer. This allows both sections to evolve independently, making the code base easier to modify. 

**Improves Maintainability** 

Since the code base is split into two sections, making changes to one part of the system is most likely not going to impact the other part. Which makes maintaining the code base easier and more efficient

**Improves Testing**

Testing is a lot easier when you have a bridge pattern in your code base because you can focus on testing the abstraction layer separately from testing the implementation layer. This allows for easier and more targeted testing. 

**Improves Readability**

The Bridge pattern creates a clear hierarchy in the code base. Organzing the code base in this way helps in understanding the relationships between different parts of the system. 

## 2.3. Example 

```javascript 
// Abstraction
class Shape {
  constructor(color) {
    this.color = color;
  }

  draw() {
    console.log(`Drawing a shape with color ${this.color}`);
  }
}

// Implementations
class RedColor {
  applyColor() {
    console.log('Applying red color');
  }
}

class BlueColor {
  applyColor() {
    console.log('Applying blue color');
  }
}

// Bridge
class ShapeWithColor extends Shape {
  constructor(color, colorImplementation) {
    super(color);
    this.colorImplementation = colorImplementation;
  }

  draw() {
    super.draw();
    this.colorImplementation.applyColor();
  }
}

// Usage
const redShape = new ShapeWithColor('red', new RedColor());
const blueShape = new ShapeWithColor('blue', new BlueColor());

redShape.draw();  // Output: Drawing a shape with color red, Applying red color
blueShape.draw(); // Output: Drawing a shape with color blue, Applying blue color
```
## 3. Composite 

The composite design pattern allows for the creation of objects with properties that are primitive items or a collection of objects. Imagine a tree like structure, where you have single objects (leaf nodes) or groups of objects (branches). The composite design pattern allows you to create this type of structure and be able to perform operations on each level in a consistent manner. 

## 3.1 Components of the Composite 

*Component*

This is the interface/class that represents both leaf nodes (individual elements) and composite nodes (collection of elements). The component defines operations that can be applied to both types of nodes. 

*Leaf*

This represents individual objects in the tree that do not have any children. They implement the operations that are defined in the component interface. 

*Composite*

This represents the composites or containers that can hold a collection of leaf nodes or other composite nodes. 


## 3.2. Benefits of Composites 

**Uniformly and Consistency** 

The Composite design pattern provides a uniform way to treat both individual objects and compositions of objects. Clients have one common interface to use to operate on these objects which simplifes the code base and object interactions. 

**Flexibility** 

This design pattern allows for flexibility in adding new types of components or modifying existing ones without affecting the client code. You can introduce new types of leaf or composite objects easily. 


**Simplified Client Code**

The client code doesn't need to distinguish between individual and composite components, making it simpler and more intuitive to work with the structure.


## 3.3. Example 

```javascript 
class SingleBlock {
  constructor(name) {
    this.name = name;
  }

  display() {
    console.log('Block:', this.name);
  }
}

class BlockCollection {
  constructor(name) {
    this.name = name;
    this.blocks = [];
  }

  add(block) {
    this.blocks.push(block);
  }

  remove(block) {
    this.blocks = this.blocks.filter(b => b !== block);
  }

  display() {
    console.log('Block Collection:', this.name);

    for (const block of this.blocks) {
      block.display();
    }
  }
}

// Usage
const block1 = new SingleBlock('Block 1');
const block2 = new SingleBlock('Block 2');
const block3 = new SingleBlock('Block 3');

const blockGroup1 = new BlockCollection('Block Group 1');
blockGroup1.add(block1);
blockGroup1.add(block2);

const blockGroup2 = new BlockCollection('Block Group 2');
blockGroup2.add(block3);

const megaStructure = new BlockCollection('Mega Structure');
megaStructure.add(blockGroup1);
megaStructure.add(blockGroup2);

megaStructure.display();
```

## 4. Decorator 

The Decorator design pattern can be used to modify an objects behavior either statically or dynamically without affecting the behavior of other objects from the same class. Decorators are particularly useful when you want to add features to an object in a flexible and reusable way. 

## 4.1. Components of a Decorator 

*Component Interface*

This defines the logic for the objects that can have resposibilities added to them dynamically. 

*Concrete Components*

This is the initial object to which additional functionalities can be added. 

*Decorator* 

This is an interface that extends the functionality of the concrete components. It has a reference to a component instance and implements the component interface. 

*Concrete Decorators*

These are the concrete implementations of the decorator class, they add specific behavior to the desired component by extending the decorator class. 


## 4.2. Benefits of Decorators 

**Extensibility and Flexibility** 

Decorators allow you to add new functionalities or behaviors to objects dynamically at runtime. This promotes extensibility without modifying the existing codebase and provides flexibility in how you can compose and use these additional functionalities.

**Modularity**

Decorators enable a more modular approach to code by breaking down functionality into smaller, more manageable units. These units can be combined and reused in various ways. 

**Runtime Configuration**

Decorators allow you to dynamically configure an object at runtime. This allows you to add or remove functionalities without impacting the core components or needing to recompile the code. 

**Reduce Subclassing**

Without Decorators, extending functionalities often involves creating numerous subclasses for each combination of behaviors. Decorators eliminate the need for subclasses which results in an cleaner and easier to understand code base. 

## 4.3. Example 

```javascript 
class Coffee {
  cost() {
    return 5;
  }
}

class MilkDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 2;
  }
}

class SugarDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 1;
  }
}

// Usage
let coffee = new Coffee();
console.log('Cost of plain coffee:', coffee.cost());

let milkCoffee = new MilkDecorator(coffee);
console.log('Cost of milk coffee:', milkCoffee.cost());

let sugarMilkCoffee = new SugarDecorator(milkCoffee);
console.log('Cost of sugar milk coffee:', sugarMilkCoffee.cost());
```

## 5. Facade 

The Facade design pattern is basically a simplified interface that the client can interact with to use other low level operations hidden elsewhere in the code base. This design pattern is often used in systems that are built around a multi-layer architecture. Facades allow the client to perform certain tasks without needing to understand the complexity of the underlying system. 


## 5.1. Components of the Facade 

*Facade*

The facade is the interface that the client will interact with. It provides a simple and unified interface that delegates the clients requests to the appropriate objects within the subsystem

*Subsystem*

The subsystem consists of all the various components and functionalities that the Facade wraps around. The subsystem and the Facade interact with eachother but operate independently. 


## 5.2. Benefits of the Facade 

**Simplified Interface**

The Facade provides a simple and easy to understand interface 

**Code Organization**

The Facade helps organize the code by encapsulating the subsystem's functionality and providing a clear separation of concerns 

**Easier Maintenance**

Changes to the subsystem can be isolated within the facade, reducing the impact on the client code. 


## 5.3. Example 

```javascript 
// Plumbing subsystem
class PlumbingSubsystem {
  constructor() {}

  turnOnWater() {
    console.log('Plumbing: Water turned on');
  }

  turnOffWater() {
    console.log('Plumbing: Water turned off');
  }
}

// Electrical subsystem
class ElectricalSubsystem {
  constructor() {}

  turnOnElectricity() {
    console.log('Electrical: Electricity turned on');
  }

  turnOffElectricity() {
    console.log('Electrical: Electricity turned off');
  }
}

// House facade
class HouseFacade {
  constructor() {
    this.plumbingSubsystem = new PlumbingSubsystem();
    this.electricalSubsystem = new ElectricalSubsystem();
  }

  enterHouse() {
    this.plumbingSubsystem.turnOnWater();
    this.electricalSubsystem.turnOnElectricity();
    console.log('You have entered the house.');
  }

  leaveHouse() {
    this.plumbingSubsystem.turnOffWater();
    this.electricalSubsystem.turnOffElectricity();
    console.log('You have left the house.');
  }
}

// Client
const client = () => {
  const house = new HouseFacade();

  // Enter the house
  house.enterHouse();

  // Leave the house
  house.leaveHouse();
};

// Run the client
client();
```

## 6. Flyweight 

The Flyweight design pattern aims to minimize memory usage or computaional expenses by storing intrinsic values (similar properties) of similar object in an application, reducing the amount of duplicate code. This is particularly useful when dealing with a large number of similar objects in an application. 

## 6.1. Components of a Flyweight 

*FlyweightFactory*

The flyweight factory creates the flyweight objects. It contains a function that will create a flyweight if one does not already exist and it stores newly created flyweights for future request. 

*Flyweight*

The flyweight contains the intrinsic data that will be shared across the application 


## 6.2. Benefits of Flyweights 

**Memory Efficiency**

By sharing intrinsic data among multiple objects, the Flyweight pattern significantly reduces memory usage especially when dealing with a large number of instances. 

**Performance Improvements** 

Due to reduced memory usage, the application's overall performance improves. Lower memory usage typically leads to faster execution times and smoother application performance. 

**Simplifies State Management**

By separating intrinsic data (shared values) and extrinisc data (unique values), Flyweights simplify the management of these states. It allows for a cleaner separation of concerns and more organized approach to state handling. 

## 6.3. Example 

```javascript 
// Flyweight object for Camera
function Camera(make, model, resolution) {
    this.make = make;
    this.model = model;
    this.resolution = resolution;
}

// Flyweight factory for Camera
var FlyWeightCameraFactory = (function () {
    var flyweights = {};

    return {
        get: function (make, model, resolution) {
            if (!flyweights[make + model]) {
                flyweights[make + model] = new Camera(make, model, resolution);
            }
            return flyweights[make + model];
        },

        getCount: function () {
            var count = 0;
            for (var f in flyweights) count++;
            return count;
        }
    };
})();

// Camera collection
function CameraCollection() {
    var cameras = {};
    var count = 0;

    return {
        add: function (make, model, resolution, serial) {
            cameras[serial] = {
                flyweight: FlyWeightCameraFactory.get(make, model, resolution),
                serial: serial
            };
            count++;
        },

        get: function (serial) {
            return cameras[serial];
        },

        getCount: function () {
            return count;
        }
    };
}

// Run the example
function run() {
    var cameras = new CameraCollection();

    cameras.add("Canon", "EOS R5", "45MP", "A1234");
    cameras.add("Nikon", "D850", "45.7MP", "B5678");
    cameras.add("Sony", "A7R III", "42.4MP", "C9101");
    cameras.add("Canon", "EOS R5", "45MP", "D1212"); // Reusing existing flyweight

    console.log("Cameras: " + cameras.getCount());
    console.log("Flyweights: " + FlyWeightCameraFactory.getCount());
}

// Run the example
run();
``` 

## 7. Proxy 

The Proxy design pattern is a structural design pattern that allows you to provide a substitute or placeholder for another object. This proxy object can control access to the original object. In Javascript, the `proxy` object is built into the language and facilitates the implementation of the Proxy design pattern. 

## 7.1. Components of the Proxy 

*Proxy*

The Proxy contains an interface that is similar to the real object, it maintains a reference that lets the proxy access the real object and it handles requests and forwards them to the real object. 

*RealSubject*

This is the actual object that the Proxy is substituting for. 

## 7.2. Benefits of Proxies

**Controlled Access** 

Proxies allow you to control access to the original object, enabling you to implement access control logic such as permissions, restrictions, or validations before allowing access to the underlying object. 

**Behavior Augmentation**

Proxies can add additional behavior or functionality before or after the invocation of methods or access to properties of the original object. This is useful for implementing cross-cutting concerns like logging, caching, or error handling.

**Caching**

Proxies can implement caching mechanism to store results of expensive operations, improving performance and efficiency 


**Lazy Initialization** 

Proxies enable lazy initialization, where you can delay the creation of the actual object until its needed. This can improve performance by reducing upfront resource usage. 

## 7.3. Example 

```javascript
// Original object representing a bank account
const bankAccount = {
  balance: 1000,

  deposit(amount) {
    this.balance += amount;
    console.log(`Deposited ${amount}. New balance: ${this.balance}`);
  },

  withdraw(amount) {
    if (amount <= this.balance) {
      this.balance -= amount;
      console.log(`Withdrew ${amount}. New balance: ${this.balance}`);
    } else {
      console.log('Insufficient funds.');
    }
  }
};

// Create a proxy for the bank account
const bankAccountProxy = new Proxy(bankAccount, {
  // Intercept property access
  get(target, property) {
    if (property === 'balance') {
      // Add some custom behavior before accessing 'balance'
      console.log('Balance accessed.');
    }
    return target[property];
  },

  // Intercept method invocation
  apply(target, thisArg, args) {
    // Add some custom behavior before invoking a method
    console.log(`Method "${args[0]}" called.`);
    return target.apply(thisArg, args);
  }
});

// Accessing the proxy
console.log(bankAccountProxy.balance); // This will trigger the custom behavior

bankAccountProxy.deposit(500); // This will trigger the custom behavior for method invocation
```
---

# Behavioral Design Patterns

Focus on how objects communicate with each other and assigning responsibilities to them.

## 1. Chain of Responsibility 

The Chain of Responsibility is a behavioural design pattern and its main purpose is to take a request and pass it along a chain of handlers. When the request goes through the chain each handler will decide either to process the request or pass it to the next handler in the chain. This pattern allows multiple handlers to handle the request without the sender needing to know which one will process it. 

## 1.1. Components of the Chain of Responsibility 

*Request*

The request is just the object the client sends that needs to be processed. The request goes through the chain of handlers until it is processed or reaches the end of the chain. 

*Abstract Handler Interface/Class*

This is the base interface/class that defines the methods that will be used for handling the request. The handler interface contains the logic for the order of the chain and how the request gets passed through.

*Concrete Handlers*

These are the methods/classes that implement the abstract handler. Each concrete handler contains logic for handling a particular type of request. If the concrete handler can process the request it will, if it can't then it will pass the request to the next handler. 

## 1.2. Benefits of the Chain of Responsibility 

**Ease of Use**

The sender does not need to know the specific method to process the request, the sender just needs to pass it to the chain. This makes it easier for the sender to process requests. 

**Flexibility and Extensibility**

New Handlers can be added to the chain or removed from the chain without modifying the sender's code. This allows for dynamic modification of the processing order. 

**Promotes Responsible Segregation**

Handlers are responsible for processing specific types of requests based on their defined logic. This promotes a clear separation of responsibilities, making it easier to manage and maintain each handler independently.

**Sequential Request Processing**

The pattern ensures that each request is processed sequentially through the chain of handlers. Each handler can choose to process the request or pass it to the next handler. This can be particularly useful in scenarios where requests need to be processed in a specific order.

## 1.3. Example 

```javascript 
// Handler interface
class CoffeeHandler {
  constructor() {
    this.nextHandler = null;
  }

  setNext(handler) {
    this.nextHandler = handler;
  }

  processRequest(request) {
    throw new Error('processRequest method must be implemented by subclasses');
  }
}

// Concrete handler for ordering coffee
class OrderCoffeeHandler extends CoffeeHandler {
  processRequest(request) {
    if (request === 'Coffee') {
      return 'Order placed for a cup of coffee.';
    } else if (this.nextHandler) {
      return this.nextHandler.processRequest(request);
    } else {
      return 'Sorry, we do not serve ' + request + '.';
    }
  }
}

// Concrete handler for preparing coffee
class PrepareCoffeeHandler extends CoffeeHandler {
  processRequest(request) {
    if (request === 'PrepareCoffee') {
      return 'Coffee is being prepared.';
    } else if (this.nextHandler) {
      return this.nextHandler.processRequest(request);
    } else {
      return 'Cannot prepare ' + request + '.';
    }
  }
}

// Client code
const orderHandler = new OrderCoffeeHandler();
const prepareHandler = new PrepareCoffeeHandler();

// Set up the chain
orderHandler.setNext(prepareHandler);

// Order coffee
console.log(orderHandler.processRequest('Coffee'));  // Output: Order placed for a cup of coffee.

// Prepare coffee
console.log(orderHandler.processRequest('PrepareCoffee'));  // Output: Coffee is being prepared.

// Try ordering something else
console.log(orderHandler.processRequest('Tea'));  // Output: Sorry, we do not serve Tea.
```

## 2. Command 

The command design pattern is a behavioral design pattern that allows you to encapsulate a request as an object, that object will contain all the necessary information for the request's execution. This pattern allows for the parameterization and queuing of requests and provides the ability to undo operations. 

## 2.1. Components of the Command 

*Invoker*

This is the object that requests the execution of a command. It has a reference to a command and can execute the command by calling its `execute` method. The Invoker does not need to know the specifics of how the command is executed. It just triggers the command. 

*Command*

This is the interface or abstract class that declares the `execute` method. It defines the common method that concrete command classes should implement.

*Receiver* 

This is an object that performs the actual work when the `execute` method of a command is called. The receiver knows how to carry out the action associate with a specific command. 

## 2.2. Benefits of the Command 


**Flexibility and Extensibility**

This pattern allows for easy addition of new commands without needing to modify the invoker or receiver. 

**Undo and Redo Operations**

The command pattern facilitates the implementation of undo and redo operations.Each command object can keep track of the previous state, enabling the reversal of the executed action.

**Parameterization and Queuing**

Commands can be parameterized with arguments, allowing for the customization of actions at runtime. Additionally, the pattern enables the queuing and scheduling of requests, providing control over the order of execution.

**History and Logging**

It's possible to maintain a history of executed commands, which can be useful for auditing, logging, or tracking user actions.

## 2.3. Example 

```javascript 

class Command {
  constructor(receiver) {
    this.receiver = receiver;
  }

  execute() {
    throw new Error('execute() method must be implemented');
  }
}

class ConcreteCommand extends Command {
  constructor(receiver, parameter) {
    super(receiver);
    this.parameter = parameter;
  }

  execute() {
    this.receiver.action(this.parameter);
  }
}

class Receiver {
  action(parameter) {
    console.log(`Receiver is performing action with parameter: ${parameter}`);
  }
}

class Invoker {
  constructor() {
    this.commands = [];
  }

  addCommand(command) {
    this.commands.push(command);
  }

  executeCommands() {
    this.commands.forEach(command => command.execute());
    this.commands = []; // Clear the executed commands
  }
}

// Usage
const receiver = new Receiver();
const command1 = new ConcreteCommand(receiver, 'Command 1 parameter');
const command2 = new ConcreteCommand(receiver, 'Command 2 parameter');

const invoker = new Invoker();
invoker.addCommand(command1);
invoker.addCommand(command2);

invoker.executeCommands();
```

## 3. Interperator 

The interperator design pattern is used to define a grammar for a language and provide an interpreter to interpret sentences in that language. It's typically use for creating language interpreters or parsers but you could also use them inside your application. Imagine you have a complex desktop application, you could design a basic scripting language which allows the end-user to manipulate your application through simple instructions. 


## 3.1. Components of the Interperator 

*Context*

A global state or context that the Interpreter uses to interpret expressions. It often contains information that is relevant during the interpretation of expressions. 

*Abstract Expressions* 

Defines an interface for all types of expressions in the language's grammar. These expressions are typically represented as an abstract class or interface. 

*Terminal Expressions*

Represents the terminal symbols in the grammar. These are the leaves of the expression tree. Terminal expression implement the interface defined by the abstract expression.

*Non-terminal Expression* 

Represents the non-terminal symbols in the grammar. Non-terminal expressions use terminal and/or other non-terminal expressions to define complex expressions by combining or composing them.

*Expression Tree* 

Represents the hierarchical structure of the language's expressions. The expression tree is built by combining terminal and non-terminal expressions based on the rules of the language's grammar. 

*Interpreter*

Defines an interface or class that interprets the abstract syntax tree created by the expression tree. It typically includes an `interpret` method that takes a context and interprets the expression based on the given context.

*client*

Builds the abstract syntax tree using terminal and non-terminal expressions based on the language's grammar. The client then uses the interpreter to interpret the expression. 

## 3.2. Benefits of Interpreters

**Ease of Grammar Interpretation**

The pattern simplifies the interpretation of complex grammatical rules by breaking them down into smaller, more manageable expressions. Each expression type handles its own interpretation, making the overall interpretation process easier to manage.

**Better Error Handling**

Since each expression type handles its own interpretation, error handling can be tailored to specific expressions. This allows for more precise and meaningful error messages when parsing or interpreting the input.

**Flexibility and Extensibility** 

The interpreter pattern provides a flexible way to define and extend grammatical rules and language expressions without modifying the core interpreter logic. You can easily add new expressions by creating new terminal and non-terminal expression classes. 

**Integration with other Design Patterns**

The Interpreter pattern can be combined with other design patterns, such as Composite, to build complex hierarchies of expressions. This allows for the creation of powerful and feature-rich interpreters.

## 3.3. Example 

```javascript 
// Abstract Expression
class Expression {
  interpret(context) {
    // To be overridden by subclasses
  }
}

// Terminal Expression: NumberExpression
class NumberExpression extends Expression {
  constructor(number) {
    super();
    this.number = number;
  }

  interpret(context) {
    return this.number;
  }
}

// Terminal Expression: VariableExpression
class VariableExpression extends Expression {
  constructor(variable) {
    super();
    this.variable = variable;
  }

  interpret(context) {
    return context[this.variable] || 0;
  }
}

// Non-terminal Expression: AddExpression
class AddExpression extends Expression {
  constructor(expression1, expression2) {
    super();
    this.expression1 = expression1;
    this.expression2 = expression2;
  }

  interpret(context) {
    return this.expression1.interpret(context) + this.expression2.interpret(context);
  }
}

// Non-terminal Expression: SubtractExpression
class SubtractExpression extends Expression {
  constructor(expression1, expression2) {
    super();
    this.expression1 = expression1;
    this.expression2 = expression2;
  }

  interpret(context) {
    return this.expression1.interpret(context) - this.expression2.interpret(context);
  }
}

// Client code
const context = { a: 10, b: 5, c: 2 };

const expression = new SubtractExpression(
  new AddExpression(
    new VariableExpression('a'),
    new VariableExpression('b')
  ),
  new VariableExpression('c')
);

const result = expression.interpret(context);
console.log('Result:', result); // Output: Result: 13
```

## 4. Iterator 

The Iterator pattern allows clients to effectively loop over a collection of objects

## 4.1. Components of the Iterator 

*Iterator*

Implements Iterator interface or class with methods like `first()`,`next()`. The Iterator keeps track of the current position when traversing collections. 

*Items*

These are the individual objects of the collection that the Iterator will traverse 

## 4.2. Benefits of iterators

**Compatibility with Different Data Structures** 

The Iterator pattern allows the same iteration logic to be applied to different data structures. 

**Support for concurrent Iteration**

Iterators can support concurrent iteration over the same collection without interfering with each other, this enables the client to iterate over the collection in different ways simultaneously.

**Lazy Loading**

Iterators can be designed to load elements on demand, which is beneficial for large collections where loading all elements at once might be impractical or resource-intensive. Elements can be fetched as needed, optimizing memory usage.

**Simplified Interface**

The Iterator pattern provides a clean and consistent interface for accessing elements in a collection without exposing the internal structure of the collection. This simplifies the usage and understanding of the collection.

## 4.3. Example 

```javascript
// Car class representing a car
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  getInfo() {
    return `${this.make} ${this.model}`;
  }
}

// Iterator interface
class Iterator {
  constructor(collection) {
    this.collection = collection;
    this.index = 0;
  }

  next() {
    return this.collection[this.index++];
  }

  hasNext() {
    return this.index < this.collection.length;
  }
}

// Collection of cars
class CarCollection {
  constructor() {
    this.cars = [];
  }

  addCar(car) {
    this.cars.push(car);
  }

  createIterator() {
    return new Iterator(this.cars);
  }
}

// Usage
const carCollection = new CarCollection();
carCollection.addCar(new Car('Toyota', 'Corolla'));
carCollection.addCar(new Car('Honda', 'Civic'));
carCollection.addCar(new Car('Ford', 'Mustang'));

const iterator = carCollection.createIterator();

while (iterator.hasNext()) {
  const car = iterator.next();
  console.log(car.getInfo());
}
```

## 5. Mediator 

The Mediator pattern acts as a middle man between a group of objects by encapsulating how these objects interact. The mediator facilitates communication between different components of a system without them needing to directly reference each other. 

## 5.1. Components of the Mediator 

*Mediator*

The mediator manages central control over operations. It contains an interface for communicating with the Colleague objects and has a reference to each Colleague object.

*Colleague*

The colleagues are the objects that are being mediated, each colleague has a reference to the mediator.

## 5.2. Benefits of the Mediator 

**Centralized Control**

Centralizing communication within the Mediator allows for better control and coordination of interactions between components. The ,Mediator can manage message distribution, prioritize messages, and apply specific logic based on the system's requirements.

**Simplified Communication**

Mediators simplify communication logic, as components send messages to the Mediator instead of dealing with the complexity of direct communication. This simplifies the interaction between components and allows for easier maintenance and updates.

**Reusability of Mediator**

The Mediator can be reused across various components and scenarios, allowing for a single point of control for different parts of the application. This reusability promotes consistency and helps in managing the communication flow efficiently.

**Promotes Maintainability**

The Mediator pattern promotes maintainability by reducing the complexity of direct inter-component communication. As the system grows, changes and updates can be made within the Mediator without affecting the individual components, making maintenance easier and less error-prone.

```javascript
var Participant = function (name) {
    this.name = name;
    this.chatroom = null;
};

Participant.prototype = {
    send: function (message, to) {
        this.chatroom.send(message, this, to);
    },
    receive: function (message, from) {
        console.log(from.name + " to " + this.name + ": " + message);
    }
};

var Chatroom = function () {
    var participants = {};

    return {

        register: function (participant) {
            participants[participant.name] = participant;
            participant.chatroom = this;
        },

        send: function (message, from, to) {
            if (to) {                      // single message
                to.receive(message, from);
            } else {                       // broadcast message
                for (key in participants) {
                    if (participants[key] !== from) {
                        participants[key].receive(message, from);
                    }
                }
            }
        }
    };
};

function run() {

    var yoko = new Participant("Yoko");
    var john = new Participant("John");
    var paul = new Participant("Paul");
    var ringo = new Participant("Ringo");

    var chatroom = new Chatroom();
    chatroom.register(yoko);
    chatroom.register(john);
    chatroom.register(paul);
    chatroom.register(ringo);

    yoko.send("All you need is love.");
    yoko.send("I love you John.");
    john.send("Hey, no need to broadcast", yoko);
    paul.send("Ha, I heard that!");
    ringo.send("Paul, what do you think?", paul);
}
```

## 6. Memento

The Memento design pattern allows an objects state to be captured and restored at a later time without exposing its internal structure. The Memento is a separate object that stores the state of the original object. 

## 6.1. Components of the Memento 

*Originator*

This is the object that gets saved. It creates a Memento object to store its internal state. 

*Memento*

The Memento is responsible for storing the state of the originator. It has methods to retrieve and set the state of the originator but does not expose the originator's internal structure. 

*Caretaker*

The caretaker is responsible for keeping track and managing the Mementos. It does not modify or inspect the contents of the Mementos

## 6.2. Benefits of the Memento 

**State Preservation and Restoration**

Mementos allow an objects internal state to be captured and restored at a later time. 

**Undo/Redo Operations**

Memento facilitates implementing undo and redo functionality easily. Since Mementos store the objects state at various points in time, you can support undoing changes made to the object or redoing changes made to the object

**Improved Performance**

Storing the object's state in a Memento allows for more efficient storage and retrieval operations compared to other approaches. 

**Flexible Design** 

It provides a flexible way to manage the history of an object's state. The caretaker can decide which states to keep and when to restore them, allowing for a customizable approach based on the application's requirements.


## 6.3. Example

```javascript
// Computer class (originator)
class Computer {
  constructor() {
    this.os = '';
    this.version = '';
  }

  setOS(os, version) {
    this.os = os;
    this.version = version;
  }

  getState() {
    return {
      os: this.os,
      version: this.version
    };
  }

  restoreState(state) {
    this.os = state.os;
    this.version = state.version;
  }
}

// Caretaker
class Caretaker {
  constructor() {
    this.mementos = {};
    this.nextKey = 1;
  }

  add(memento) {
    const key = this.nextKey++;
    this.mementos[key] = memento;
    return key;
  }

  get(key) {
    return this.mementos[key];
  }
}

function run() {
  const computer = new Computer();
  const caretaker = new Caretaker();

  // Save state
  const originalState = computer.getState();
  const key = caretaker.add(originalState);

  // Mess up the state
  computer.setOS('Windows', '11');

  // Restore original state
  const restoredState = caretaker.get(key);
  computer.restoreState(restoredState);

  console.log(computer.getState()); // Output: { os: '', version: '' }
}

run();
```

## 7. Observer

The observer pattern allows many objects to subscribe to events that are broadcast by another object. 

## 7.1. Components of the Observer 

*Subject*

The subject is an object that implements an interface that lets observer objects subscribe to it and send notifications to observers when its state changes. 

*Observers*

The Observer subscribes to the subject and and typically has a function that get invoked when notified by the Subject

## 7.2. Benefits of Observers 

**Simplified Event Handling**

The Observer pattern can simplify event handling mechanisms, as events can be treated as notifications to observers about a state change.

**Reduces Duplicate code**

Instead of duplicating the same code to respond to state changes in multiple places, the Observer pattern allows for a centralized place to manage these responses, promoting cleaner and more maintainable code.

**Support for Broadcast Communication**

The Observer pattern facilitates a "one-to-many" communication model, where a single event triggers actions in multiple observers. This is useful in scenarios where multiple components need to react to a change in state.

**Modularity and Resuability**

Observers can be reused across different subjects, promoting modularity and code reusability. This allows for more flexible and maintainable code.

## 7.3. Example 

```javascript
function Click() {
    this.handlers = [];  // observers
}

Click.prototype = {

    subscribe: function (fn) {
        this.handlers.push(fn);
    },

    unsubscribe: function (fn) {
        this.handlers = this.handlers.filter(
            function (item) {
                if (item !== fn) {
                    return item;
                }
            }
        );
    },

    fire: function (o, thisObj) {
        var scope = thisObj || window;
        this.handlers.forEach(function (item) {
            item.call(scope, o);
        });
    }
}

function run() {

    var clickHandler = function (item) {
        console.log("fired: " + item);
    };

    var click = new Click();

    click.subscribe(clickHandler);
    click.fire('event #1');
    click.unsubscribe(clickHandler);
    click.fire('event #2');
    click.subscribe(clickHandler);
    click.fire('event #3');
}
```

## 8. State

The State pattern is a behavioral design pattern that allows you to have a base object and provide it with additional functionality based on its state. This pattern is particularly useful when an object needs to change its behavior based on its internal state.

## 8.1. Components of the State

*State*

This is the object that encapsulates the State values and the associated behavior of the State. 

*Context*

This is the object that maintains a reference to a State object that defines the current State. It also includes an interface that allows other State objects to change its current State to a different State.

## 8.2. Benefits of the State

**Modular and Organized Code**

Each State is encapuslated within its own class, making the code modular and easy to manage. 

**No Need for Switch Statements**

Switch statements can also be used to change the behavior of an object but the problem with this method is that switch statements can become very lengthy as your project scales. The State pattern fixes this issue. 

**Promotes Reusability**

States can be reused across different contexts, this reduces code duplication. 

**Simplifies Testing**

Testing individual state classes in isolation is easier and more effective than testing a monolithic object with complex conditional logic. 

## 8.3. Example 

```javascript 
class Car {
  constructor() {
    this.state = new ParkState();
  }

  setState(state) {
    this.state = state;
    console.log(`Changed state to: ${state.constructor.name}`);
  }

  park() {
    this.state.park(this);
  }

  drive() {
    this.state.drive(this);
  }

  reverse() {
    this.state.reverse(this);
  }
}

class ParkState {
  park(car) {
    console.log("Car is already in Park");
  }

  drive(car) {
    console.log("Shifting to Drive");
    car.setState(new DriveState());
  }

  reverse(car) {
    console.log("Shifting to Reverse");
    car.setState(new ReverseState());
  }
}

class DriveState {
  park(car) {
    console.log("Shifting to Park");
    car.setState(new ParkState());
  }

  drive(car) {
    console.log("Car is already in Drive");
  }

  reverse(car) {
    console.log("Shifting to Reverse");
    car.setState(new ReverseState());
  }
}

class ReverseState {
  park(car) {
    console.log("Shifting to Park");
    car.setState(new ParkState());
  }

  drive(car) {
    console.log("Shifting to Drive");
    car.setState(new DriveState());
  }

  reverse(car) {
    console.log("Car is already in Reverse");
  }
}

// Example usage
const car = new Car();

car.drive();
car.reverse();
car.drive();
car.park();
car.drive();  // Trying to drive while parked
```

## 9. Strategy 

The Strategy pattern is essentially a design pattern that allows you to have a group of algorithms (strategies) that are interchangeable. 

## 9.1. Components of Strategy 

*Strategy*

This is an algorithm that implements the Strategy interface. 

*Context*

This is the object that maintains a reference to the current strategy. It defines an interface that allows the client to change the current Strategy to a different Strategy or retrieve calculations from the current Strategy referenced. 

## 9.2. Benefits of Strategy 

**Dynamically Swappable Algorithms**

Strategies can be swapped at runtime, allowing for dynamic selection of algorithms based on different conditions or requirements. This is particularly useful when the appropriate algorithm may vary based on user input, configuration settings, or other factors.

**Flexibility and Maintainability**

Strategies can be changed or extended without modifying the context using them. This makes the system more flexible and easier to maintain since changes in one strategy do not affect others.

**Simplifies Testing**

Testing strategies in isolation is easier since each strategy is a separate class. This allows for targeted testing and ensures that changes to one strategy don't inadvertently affect others.

**Reusability**

Strategies can be reused in multiple contexts or applications, promoting code reuse and minimizing redundancy.

## 9.3. Example

```javascript 
class RegularCustomerStrategy {
  calculatePrice(bookPrice) {
    // Regular customers get a fixed discount of 10%
    return bookPrice * 0.9;
  }
}

class VIPCustomerStrategy {
  calculatePrice(bookPrice) {
    // VIP customers get a fixed discount of 20%
    return bookPrice * 0.8;
  }
}

class BookStore {
  constructor(pricingStrategy) {
    this.pricingStrategy = pricingStrategy;
  }

  setPricingStrategy(pricingStrategy) {
    this.pricingStrategy = pricingStrategy;
  }

  calculatePrice(bookPrice) {
    return this.pricingStrategy.calculatePrice(bookPrice);
  }
}

// Usage
const regularCustomerStrategy = new RegularCustomerStrategy();
const vipCustomerStrategy = new VIPCustomerStrategy();

const bookstore = new BookStore(regularCustomerStrategy);

console.log('Regular customer price:', bookstore.calculatePrice(50)); // Outputs: 45 (10% discount)
bookstore.setPricingStrategy(vipCustomerStrategy);
console.log('VIP customer price:', bookstore.calculatePrice(50)); // Outputs: 40 (20% discount)
```

## 10. Template Method 

The Template Method is a behavioral design pattern that defines the program skeleton of an algorithm in a method but lets subclasses override specific steps of the algorithm without changing its structure. 

## 10.1. Components of the Template Method 

*Abstract Class*

The abstract class is the template for the algorithm. It defines an interface for the client to invoke its method. It also contains all the functions that can be overridden by subclasses.

*Concrete Class*

Implements the steps as defined in the Abstract Class and can make changes to the steps. 

## 10.2. Benefits of the Template Method 

**Code Reusability**

The pattern promotes code reusability by defining the algorithm's skeleton in a base class. Subclasses can reuse this structure and only need to provide implementations for specific steps.

**Easy Maintenance**

Making changes to the algorithm is simplified because modifications only need to be made in one place—the template method in the abstract class—rather than in multiple subclasses. This reduces the chances of errors and makes maintenance more straightforward.

**Extension and Variation**

The pattern allows for easy extension and variation of the algorithm. Subclasses can override certain steps to provide custom implementations, effectively extending or modifying the behavior of the algorithm without altering its core structure.

**Control Flow**

The template method defines the control flow of the algorithm, making it easier to manage and understand the sequence of operations in the algorithm.

## 10.3. Example 

```javascript 
class Camera {
  // Template method defining the common steps for capturing a photo
  capturePhoto() {
    this.turnOn();
    this.initialize();
    this.setExposure();
    this.capture();
    this.turnOff();
  }

  // Common steps for turning on the camera
  turnOn() {
    console.log('Turning on the camera');
  }

  // Abstract method for initializing the camera (to be overridden by subclasses)
  initialize() {
    throw new Error('Abstract method: initialize() must be implemented by subclasses');
  }

  // Abstract method for setting exposure (to be overridden by subclasses)
  setExposure() {
    throw new Error('Abstract method: setExposure() must be implemented by subclasses');
  }

  // Common steps for capturing a photo
  capture() {
    console.log('Capturing a photo');
  }

  // Common steps for turning off the camera
  turnOff() {
    console.log('Turning off the camera');
  }
}

class DSLRCamera extends Camera {
  initialize() {
    console.log('Initializing DSLR camera');
  }

  setExposure() {
    console.log('Setting exposure for DSLR camera');
  }
}

class MirrorlessCamera extends Camera {
  initialize() {
    console.log('Initializing mirrorless camera');
  }

  setExposure() {
    console.log('Setting exposure for mirrorless camera');
  }
}

// Usage
const dslrCamera = new DSLRCamera();
console.log('Capturing photo with DSLR camera:');
dslrCamera.capturePhoto();
console.log('');

const mirrorlessCamera = new MirrorlessCamera();
console.log('Capturing photo with mirrorless camera:');
mirrorlessCamera.capturePhoto();
```

## 11. Visitor 

The visitor design pattern is a behavioral design pattern that allows you to separate algorithms or operations from the object on which they operate. 

## 11.1 Components of the Visitor 

*ObjectStructure*

Maintains a collection of Elements which can be iterated over. 

*Elements*

The element contains an accept method that accepts the visitor objects.

*Visitor*

Implements a visit method where the argument of the method is the element being visited. This is how changes to the element get made. 

## 11.2. Benefits of the Visitor 

**Open/Closed Principle**

The pattern aligns with the Open/Closed Principle, which states that software entities (classes, modules, functions) should be open for extension but closed for modification. You can introduce new operations (new visitors) without modifying the existing object structure or elements.

**Extensibility**

You can introduce new behaviors or operations by adding new visitor implementations without modifying the existing elements or the object structure. This makes the system more extensible, allowing for new features or behaviors to be added easily.

**Centralized Behavior**

The Visitor pattern centralizes behavior-related code within the visitor classes. Each visitor encapsulates a specific behavior, which can be reused across different elements, promoting code reuse and modularity.

**Consistency in Operations**

With the Visitor pattern, you can ensure that a specific operation (visitor method) is applied consistently across various elements, as each element's accept method calls the appropriate visitor method for that element type.

## 11.3 Example 

```javascript 
class GymMember {
    constructor(name, subscriptionType, fitnessScore) {
        this.name = name;
        this.subscriptionType = subscriptionType;
        this.fitnessScore = fitnessScore;
    }

    accept(visitor) {
        visitor.visit(this);
    }

    getName() {
        return this.name;
    }

    getSubscriptionType() {
        return this.subscriptionType;
    }

    getFitnessScore() {
        return this.fitnessScore;
    }

    setFitnessScore(score) {
        this.fitnessScore = score;
    }
}

class FitnessEvaluation {
    visit(member) {
        member.setFitnessScore(member.getFitnessScore() + 10);
    }
}

class MembershipDiscount {
    visit(member) {
        if (member.getSubscriptionType() === 'Premium') {
            console.log(`${member.getName()}: Fitness score - ${member.getFitnessScore()}, Membership type - ${member.getSubscriptionType()}, Eligible for a 10% discount!`);
        } else {
            console.log(`${member.getName()}: Fitness score - ${member.getFitnessScore()}, Membership type - ${member.getSubscriptionType()}, Not eligible for a discount.`);
        }
    }
}

function run() {
    const gymMembers = [
        new GymMember("Alice", "Basic", 80),
        new GymMember("Bob", "Premium", 90),
        new GymMember("Eve", "Basic", 85)
    ];

    const fitnessEvaluation = new FitnessEvaluation();
    const membershipDiscount = new MembershipDiscount();

    for (let i = 0; i < gymMembers.length; i++) {
        const member = gymMembers[i];

        member.accept(fitnessEvaluation);
        member.accept(membershipDiscount);
    }
}

run();
```
 
 ---

