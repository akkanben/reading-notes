# Reading Notes 01 - Java Basics

## Java Basics

From [Oracle's Java Documentation](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)

### Variables

- **Instance Variables** are variables not using the *static* keyword and are unique to each instance of a class.
- **Class Variables** are variables that use the *static* keyword indicating a variable that has only one instance but is shared among instances of the class.
- **Local Variables** are variables whose scope is the method that they belong to.
- **Parameters** are variables that a method may take as input in its definition.

Variable naming in Java requires that variables begin with a letter, a dollar sign or the underscore character. Conventionally we should always begin variables with a letter and avoid using dollar signs altogether. Camel-case and self-documenting variable names is also recommended.

#### Primitive Data Types

| Name    | Default Value | Size          |
| ------- | ------------- | ------------- |
| byte    | 0             | 8-bit signed  |
| short   | 0             | 16-bit signed |
| int     | 0             | 32-bit signed |
| long    | 0L            | 64-bit signed |
| float   | 0.0f          | 32-bit        |
| double  | 0.0d          | 64-bit        |
| char    | \u0000        | 16-bit        |
| boolean | false         | 1-bit-ish     |
| String  | null          | not actually primitive |

- A literal variable is not an object and the new keyword is not used to initialize them.
- Integer literals end with an 'L' and are of type long.
- Prefixing an integer with '0x' is used for hexadecimal notation.
- Prefixing an integer with '0b' is used for binary notation.
- A floating point literal ends with the letter 'f'.
- Unicode escape sequences can be used as chars.
- Underscores can be used between digits of a numerical literal to help with readability.

#### Arrays

Arrays hold a fixed number of elements of a single type. The size is declared when the array is created. Array elements can be created in groups with curly bracket notation or individual indexes can be assigned with square bracket notation. Multidimensional arrays can be created by including more sets of square brackets. 

A Few Array Examples:
```java
class Example {
  public static void main(String[] args) {
    int[] myArray;
    myArray = new int[5]; // assign the size but leave it empty
    myArray[0] = 5;
    char[] myOtherArray = {'A', 'B', 'C'}; // assign the size and elements all at once
    boolean[][] myMatrix = {true, true}, {false, false}; // two-dimentional array
  }
}
```

Java includes a number of useful methods when working with arrays:

- `arraycopy` used to copy a range of indexes from one array to another existing array
- `copyOfRange` used to return a new array copied from a range of indexes of another array
- `binarySearch` returns an index when searching for a value
- `equals` compares two arrays for equality
- `fill` fills an array with a specific value
- `sort` sorts an array into ascending order
- `parallelSort` sorts but uses more than one processor for better speed
- `stream` create stream with an array as its source
- `toString` converts an array to string

### Operators

Java operator's order of precedence:

1. postfix
  - `expr++` increments value by 1, evaluates to original value
  - `expr--` decrements value by 1, evaluates to original value
2. unary
  - `++expr` increments value by 1, evaluates to incremented value
  - `--expr` decrements value by 1, evaluates to decremented value
  - `+expr` indicates positive value
  - `-expr` negates an expression
  - `~` inverts a bit pattern e.g. 0b0010 --> 0b1101
  - `!` 
3. multiplicative
  - `*` multiplication
  - `/` division
  - `%` modulus (remainder)
4. additive
  - `+` adding and String concatenation
  - `-` subtraction
5. shift
  - `<<` shifts bits to left e.g. 0b0010 --> 0b0100
  - `>>` shifts bits to left e.g. 0b0010 --> 0b0001
  - `>>>`
6. relational
  - `<` less than
  - `>` greater than
  - `<=` less than or equal to
  - `>=` greater than or equal to
  - `instanceof` test if object is instance of a class
7. equality
  - `==` equal to
  - `!=` not equal to
8. bitwise AND
  - `&` result has 1 bit in the positions that both values have 1 bit 
  - e.g. 0b0010 & 0b1010 --> 0b0010
9. bitwise exclusive OR
  - `^` result has 1 bit in the positions that the values differ
  - e.g. 0b0010 ^ 0b1010 --> 0b1000
10. bitwise inclusive OR
  - `|` result has 1 bit in the positions that either value has 1 bit
  - e.g. 0b0010 | 0b1010 --> 0b1010
11. logical AND
  - `&&` evaluates true if both expressions evaluate true
12. logical OR
  - `||` evaluates true if one of the expressions evaluate to true
13. ternary
  - `? :` shortcut for if/else, useful in return expressions
14. assignment
  - `=` assigns symbol on the left to the expression on the right
  - `+=` same as x = x + expr
  - `-=` same as x = x - expr
  - `*=` same as x = x * expr
  - `/=` same as x = x / expr 
  - `%=` same as x = x % expr 
  - `&=` same as x = x & expr 
  - `^=` same as x = x ^ expr
  - `|=` same as x = x | expr
  - `<<=` same as x = x << expr
  - `>>=` same as x = x >> expr
  - `>>>=` same as x = x >>> expr

### Expressions, Statements, and Blocks 

**Expressions** are made of variables, operators and methods that evaluate to a single value

**Statements** are like sentences in Java code that are punctuated by a semicolon.

**Blocks** are sections of code that begin with an open curly brace and end with and closing curly brace. Blocks can contain 0 or more statements.

### Control Flow Statements 

#### If-Then and If-Then Else Statements

If-then statements control the flow of the program by executing certain code only if a test evaluates to true. Else is used as an alternate route if the test evaluates to false.

#### Switch Statement

Switch statements use one or more cases that behave like a series of if-then tests. A default case can be used to catch anything that fails all previous tests.

#### While and Do While Statements

While statements execute a block of code until a test is false. Do-while tests execute a block of code at least once and then behave just like a while statement.

#### For Statement

The for statement is used to iterate over a range of values. There are two styles of for loops, the first uses an initialization, test, and increment to process a block. The second style is designed for iterating through collections and arrays and a variable holds the value of each element in the collection/array and the loop iterates through the entire collection/array.

#### Branching Statements

The **break** statement can be used to escape a control loop.

The **continue** statement jumps to the beginning of the control loop skipping anything that came after it.

The **return** statement exits the current method and returns a value the method expects or nothing in the case of a void method.

## Compiling Code

From [user ajswdf on reddit](https://www.reddit.com/r/explainlikeimfive/comments/233dq5/eli5_what_does_it_mean_to_compile_code/)

Compiling code is when the computer (a compiler) takes the code a programmer has written and transforms it into something the computer can understand and execute directly. The compiler will catch syntax errors and other issues that could cause the program to crash. Finding these types of issues will stop the compiling process and require the programmer to fix the problem before the code can be compiled.

## XKCD:Compiling

Cute [comic](https://xkcd.com/303/)! Shows us that there is not much the developer can do while the code is compiling, just wait for it to complete.

## Reading Java Documentation

(this article seems to be missing, the [link](https://www.dummies.com/category/articles/java-33602) just takes me to a list of articles from Dummies, none of them seem to match this topic)
