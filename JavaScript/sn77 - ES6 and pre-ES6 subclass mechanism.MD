Prior to ES6, JavaScript did not have a straightforward mechanism for creating subclasses that could effectively invoke both the constructor and methods of a superclass. This led to complex patterns and workarounds to achieve what modern class-based languages like Java or Python provide natively.

### Pre-ES6 Subclassing Challenges
1. **Calling Superclass Constructor**:
   Without a `super` keyword, you needed to manually call the superclass constructor from within the subclass constructor, often using `.call()` or `.apply()`. For example:
   ```javascript
   function Superclass(name) {
       this.name = name;
   }

   function Subclass(name, age) {
       Superclass.call(this, name); // Manually call the parent constructor
       this.age = age;
   }
   ```

2. **Linking Prototypes**:
   To ensure the subclass inherited methods from the superclass, you had to manually set up the prototype chain:
   ```javascript
   Subclass.prototype = Object.create(Superclass.prototype);
   Subclass.prototype.constructor = Subclass;
   ```

3. **Maintaining Correct `instanceof` Behavior**:
   You had to take extra care to ensure the `instanceof` operator worked correctly for instances of subclasses.

4. **Complexity with Method Overriding**:
   Overriding superclass methods often required explicitly invoking the superclass method inside the overridden one:
   ```javascript
   Subclass.prototype.method = function() {
       Superclass.prototype.method.call(this);
       // Subclass-specific logic
   };
   ```

### Post-ES6 Solution
ES6 introduced the `class` syntax, making subclassing much simpler and more intuitive:
- **`extends` Keyword**:
   This automatically links the prototype chain.
   ```javascript
   class Superclass {
       constructor(name) {
           this.name = name;
       }
   }

   class Subclass extends Superclass {
       constructor(name, age) {
           super(name); // Calls the superclass constructor
           this.age = age;
       }
   }
   ```
- **`super` Keyword**:
   - In constructors: `super()` calls the superclass constructor.
   - In methods: `super.method()` invokes a method from the superclass.

With this syntax:
1. You no longer need to manually link prototypes or set constructors.
2. The `super` keyword provides direct access to the superclass's methods and constructor.
3. Subclassing behavior is more consistent and less error-prone.

### Example Comparing Pre-ES6 and ES6
#### Pre-ES6:
```javascript
function Animal(name) {
    this.name = name;
}

Animal.prototype.speak = function() {
    console.log(`${this.name} makes a noise.`);
};

function Dog(name) {
    Animal.call(this, name); // Call superclass constructor
}

Dog.prototype = Object.create(Animal.prototype); // Link prototype chain
Dog.prototype.constructor = Dog;

Dog.prototype.speak = function() {
    Animal.prototype.speak.call(this); // Call superclass method
    console.log(`${this.name} barks.`);
};

const dog = new Dog('Rex');
dog.speak();
```

#### ES6:
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}

class Dog extends Animal {
    speak() {
        super.speak(); // Call superclass method
        console.log(`${this.name} barks.`);
    }
}

const dog = new Dog('Rex');
dog.speak();
```

The ES6 example is cleaner and avoids the boilerplate of manual prototype linking and method overrides. This improved subclassing mechanism simplifies code and aligns JavaScript with other object-oriented languages.
