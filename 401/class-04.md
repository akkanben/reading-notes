# Reading Notes 04 -- OOP

## Object-Oriented Programming Concepts

From [Oracle's Java Documentation](https://docs.oracle.com/javase/tutorial/java/concepts/)

**Objects** as a concept in software are designed to be similar to real world objects. Objects have fields that are certain properties or state that the object has. And objects can have methods that represent the objects behaviors. Bundling code into a single object has a few benefits:

  - The code is modular and can be independent from other source code.
  - Details of how the object works can be abstracted away.
  - Objects can be reused in more than one program.

**Classes** are like blueprints used to create objects of their kind. Classes are a code block that contains details about how objects are made and what their capabilities and defaults are.

## Java Classes

From [Oracle's Java Documentation](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html)

- Declare a class by using the `class` keyword. 
- Classes can extend a superclass with the `extends` keyword
- Classes can implement interfaces using the `implements` keyword. 
- Class member variable can be defined by using a feild's type and the feild's name. They can also be preceded by zero or more modifiers e.g. public, private.

The **public** modifier makes the field accessible from all classes.
The **private** modifier makes the field accessible from within its own class.

Class member methods consist of (in order) modifiers, a return type, the method's name, a list of parameters, an exception list and the method body.

- Method names should be verbs by convention.
- Methods can be overloaded when different parameter types or options are needed.

Classes can have a **constructor** method that is used when objects of their type are instantiated. The constructor has the same name as the class and has no return type.

- Objects can be instantiated from a class by using the `new` keyword.
- Classes can have multiple constructors with differing parameter requirements.

Class example from the Oracle Docs:

```java
public class Bicycle {
    public int cadence;
    public int gear;
    public int speed;
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
    public void setCadence(int newValue) {
        cadence = newValue;
    }
    public void setGear(int newValue) {
        gear = newValue;
    }
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
    public void speedUp(int increment) {
        speed += increment;
    }
}
```

### Misc 

- Varargs can be used when the number of parameters is not known -- in use it has to be used on the last parameter. Use the type followed by `...`. The parameters are accessible with array notation.
- Primitives are passed by value.
- Objects are also passed by value so if the object is reassigned to a new object that reference won't be permanent but changes to the objects properties/fields will be permanent.
- When no constructor is in the class the default constructor calls the parent's no-argument constructor, or the Object constructor if the class has no parent.
- Object fields and methods are referenced with dot notation.
- Java uses a garbage collector that frees memory used by objects when they are no longer referenced. The garbage collector works automatically when it determines the time is right.
- The `this` keyword is a reference to the current object and used to avoid shadowing in the constructor.

Access Levels

| Modifier    | Class | Package | Subclass | World|
| ----------- | ----- | ------- | -------- | ---- |
| public      |   Y   |    Y    |    Y     |   Y  |
| protected   |   Y   |    Y    |    Y     |   N  |
| no modifier |   Y   |    Y    |    N     |   N  |
| private     |   Y   |    N    |    N     |   N  |

The `static` keyword is used to define fields and methods that belong to the class itself not to instances of the class. Each instantiated object will not have it's own version of this static field or method, instead it lives in the class and is referenced with dot notation using the class name not an object's name.

The `final` modifier is used to define constants and indicates that the value of the field can not change.

Initializing a class field can be done in a single line, but if a more complicated setup is required code blocks can be used. The static keyword can precede the block if the field is to be static. Alternatively a field could be initialized to a static or non static method's return.


## Binary, Decimal and Hexadecimal Numbers

From [Math is Fun](https://www.mathsisfun.com/binary-decimal-hexadecimal.html)

Binary numbers are base 2 numbers and each position can be either a 0 or a 1. Instead of 1s, 10s, 100s, 1,000s positions found in the decimal system binary numbers follow a exponents of 2 pattern 1s, 2s, 4s, 8s, 16s, 32s etc.

Hexadecimal numbers are another number system. Hex numbers use base 16. Since there are only 9 numerals to use hexadecimal numbers use A-F to cover 10 through 15.


