# SOLID Principles

## Single Responsibility Principle

- **A class should have only one reason to change**
- A class should have only one job.

```js
class Add {
  add(a, b) {
    return a + b;
  }
}

class Multiply {
  multiply(a, b) {
    return a * b;
  }
}

// consuming the classes
const add = new Add();
const multiply = new Multiply();
```

## Open/Closed Principle

- **Open for extension, closed for modification**
- Software entities should be open for extension, but closed for modification.
- The goal is to allow the introduction of new features without changing existing code.

```js
class Shape {
  area() {
    throw new Error("You have to implement the method area!");
  }
}

class Square extends Shape {
  constructor(size) {
    super();
    this.size = size;
  }

  area() {
    return this.size ** 2;
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  area() {
    return Math.PI * this.radius ** 2;
  }
}

//consuming the classes
const square = new Square(5);
const circle = new Circle(5);
```

## Liskov Substitution Principle

- **Derived types must be completely substitutable for their base types**
- Objects of a superclass shall be replaceable with objects of its subclass without affecting the functionality of the program.

```js
class Animal {
  walk() {
    console.log("Walking...");
  }
}

class Bird extends Animal {
  fly() {
    console.log("Flying...");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Barking...");
  }
}

// consuming the classes
const parrot = new Bird();
parrot.walk(); // extensing the features from superclass
parrot.fly();
```

## Interface Segregation Principle

- **A client should never be forced to implement an interface that it doesn't use or clients shouldn't be forced to depend on methods they do not use.**
- Many client-specific interfaces are better than one general-purpose interface.

```js
class DrivingTest {
  constructor(driver) {
    this.driver = driver;
  }

  test() {
    this.driver.drive();
  }
}

class CarDrivingTest extends DrivingTest {
  constructor(driver) {
    super(driver);
  }
  startCarDrivingTest() {
    return "Car driving test started";
  }
  startTruckDrivingTest() {
    return null;
  }
}
```

## Dependency Inversion Principle

- **High-level modules should not depend on low-level modules. Both should depend on abstractions.**
- Abstractions should not depend on details. Details should depend on abstractions.

```js
class EmailController {
  sendEmail(emailDetails) {
    if (res.status === 200) {
      return true;
    }
    return false;
  }
}

class EmailApiController {
  constructor(emailController) {
    this.emailController = emailController;
  }

  sendEmail(emailDetails) {
    return this.emailController.sendEmail(emailDetails);
  }
}
```
