# Reading Notes 06 -- Inheritance and Interfaces

[Java Docs](https://docs.oracle.com/javase/tutorial/java/IandI/index.html)
[More Java Docs](https://docs.oracle.com/javase/tutorial/java/concepts/)

## Interfaces

In general an interface is a group of related methods without an implementation. Classes can extend interfaces (one or more than one) and if they do they must implement all the methods of the interface. Interfaces can be used to define how software interacts and allows groups of coders to share a group of methods without knowing how the other's code works.

More precisely interfaces *can* have method definitions, but only of *default methods* and *static methods* but any other method type must be implemented by the class that extends it. 

- Interfaces can be evolved by designing a new interface that extends the earlier. Classes that use the newer interface can still access the earlier version. 
- Interface **default methods** have a body and can be called from an instantiation of a class that extends the interface. Default methods allow programmers to add new functionality to existing interfaces.
- Static methods in interfaces can also have a body and they can be used to help organize methods that make more sense existing in the interface rather than a separate class.
- An interface name can be used anywhere a type can be used.

## Inheritance

Inheritance allows new classes to reuse properties and methods from existing classes. Subclasses can have subclasses and a whole hierarchy can be created. Subclasses can have their own properties and methods and they can also override an existing method (polymorphism).

- Constructors are not inherited, but subclasses can call their superclass' constructor.
- A subclass with a static method of the same signature of it's superclass will hide it.
- **Final** methods can not be overridden by a subclass.
- **Abstract** methods are declared without a definition -- similar to methods in an interface.

Abstract classes and interfaces have a lot of similarities. Abstract classes can not be instantiated but they can be subclassed. Abstract classes work well to tie together a group of closely related classes

### Packages

Packages are folders that hold collections of classes and interfaces. Packages create a name-space that is confined to the package and prevents name conflicts.
