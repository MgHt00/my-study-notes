An **abstract class** is a class that serves as a template or blueprint for other classes. It is not intended to be instantiated directly, but instead to be subclassed, where the subclasses provide concrete implementations for abstract methods or extend its functionality.

In JavaScript, while there is no built-in keyword like `abstract` (as seen in some other programming languages), you can create abstract-like behavior using regular classes and methods that throw errors if not implemented by a subclass.

### Example: Abstract Class in JavaScript

Here’s how you can define and use an abstract-like class:

```javascript
class Shape {
  constructor(name) {
    if (new.target === Shape) {
      throw new Error("Shape is an abstract class and cannot be instantiated directly.");
    }
    this.name = name;
  }

  // Abstract method: Subclasses must implement this
  area() {
    throw new Error("The area() method must be implemented by subclasses.");
  }

  // Shared method for all subclasses
  describe() {
    return `This is a shape called ${this.name}.`;
  }
}

// Subclass of Shape
class Circle extends Shape {
  constructor(radius) {
    super("Circle");
    this.radius = radius;
  }

  // Implementing the abstract method
  area() {
    return Math.PI * this.radius ** 2;
  }
}

// Subclass of Shape
class Rectangle extends Shape {
  constructor(width, height) {
    super("Rectangle");
    this.width = width;
    this.height = height;
  }

  // Implementing the abstract method
  area() {
    return this.width * this.height;
  }
}

// Usage
try {
  const shape = new Shape(); // Throws error: Cannot instantiate abstract class
} catch (e) {
  console.log(e.message);
}

const circle = new Circle(5);
console.log(circle.describe()); // "This is a shape called Circle."
console.log(`Area of Circle: ${circle.area()}`); // Area of Circle: 78.54...

const rectangle = new Rectangle(4, 6);
console.log(rectangle.describe()); // "This is a shape called Rectangle."
console.log(`Area of Rectangle: ${rectangle.area()}`); // Area of Rectangle: 24
```

### Key Points in the Example:
1. **Abstract Class Behavior**:
   - The `Shape` class cannot be instantiated directly because the constructor checks `new.target`.
   - The `area()` method is intentionally left unimplemented in the `Shape` class, and it throws an error if a subclass does not override it.

2. **Subclasses**:
   - `Circle` and `Rectangle` are subclasses that inherit from `Shape`. 
   - Both subclasses implement the `area()` method specific to their geometry.

3. **Shared Implementation**:
   - The `describe()` method is shared among all subclasses because it provides generic functionality that applies to all shapes.

### Why Use Abstract Classes?
- **Code Reusability**: Abstract classes allow shared functionality (like `describe`) to be defined once, reducing duplication.
- **Encapsulation**: Abstract methods enforce a contract that all subclasses must follow.
- **Flexibility**: You can define a structure for related classes while allowing them to customize their behavior as needed.

This pattern is especially useful in object-oriented programming scenarios where you need to group related subclasses under a common umbrella.
