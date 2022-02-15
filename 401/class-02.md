# Reading Notes 02 - Arrays, Loops, Imports

## Java Imports

From the [Java Notes section from ENSTA Paris](https://perso.ensta-paris.fr/~diam/java/online/notes-java/language/10basics/import.html) 

Java classes can be grouped together into directories refered to as **packages**. An optional package declaration can be added to the top of a source file. A java file in a folder named "basics" could be declared `package basics;`.

The imports section follows the optional package declaration section. Imports can be made with the `import` keyword followed by the package to be imported. 

- The asterix `*` wildcard character can be used to make all classes inside a package availible e.g. `import java.time.format.*;`
- Instead of importing needed classes can be used fully qualified e.g. `java.util.Random rand = new java.util.Random();`

### Other Notes

- Importing does not increase the size of the java executable, it just shows the compiler where to look.
- There isn't any advantage to importing less classes or importing them explicit instead of using a wildcard.
- The classes in the java.lang package are visible by default.

