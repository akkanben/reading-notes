Reading Notes 09 - Functional Programming

## Functional Programming

### Questions

Medium article from [The Renaissance Developer](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)

1. What is functional programming?
  - Functional programming is a declarative programming paradigm where functions are first-class citizens and can be assigned to names and passed to other functions.  
2. What is a pure function and how do we know if something is a pure function?
  - A pure function should be deterministic, always return the same if given the same arguments, it shouldn't contain any global variables the could be changed and it should not cause any side effects.
3. What are the benefits of a pure function?
  - It's easier to test and get repeatable results and it can be easier to understand a program.
4. What is immutability?
  - This describes unchanging data. Data that can not change or should not change. To change an immutable piece of data we need to create a new item with the same value.
5. What is Referential transparency?
  - Referential transparency is the result of pure functions and immutable data, this allows us to memoize data for optimization.


## Modules and require()

YouTube Video from [The Net Ninja](https://www.youtube.com/watch?v=xHLd36QoS4k)

### Questions


1. What is a module?
  - A module in Node.js is just a Javascript file. Parts of a project or classes can be organized in separate modules.
2. What does the word ‘require’ do?
  - The word require is a global function that can be used to asign an exported bit of code to a variable in another file that we can use.
3. How do we bring another module into the file the we are working in?
  - We asign a variable to the require() function and pass in the file that has the exported code we want.
4. What do we have to do to make a module available?
  - To make a module available we need to identify the part of code we want to export.

## Things I want to know more about

- Functional programming is really intriguing, I'm definitely going to put some time into learning more.
