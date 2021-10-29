# Reading Notes 05 - Putting it all Together

## Think Reat-y

From the [React Docs - Thinking in React](https://reactjs.org/docs/thinking-in-react.html)

### Questions

1. What is the `single responsibility principle` and how does it apply to components?
  - Each component should preform a single piece of functionality, this will help make the app more modular.
2. What does it mean to build a ‘static’ version of your application?
  - A version of the app with no interaction, the React component will only have a render() function.
3. Once you have a static application, what do you need to add?
  - You need to decide what the minimum amount of state needed to represent the app's UI.
4. What are the three questions you can ask to determine if something is state? Likely not state if yes:
  - Does it get passed via props?
  - Can it stay constant? 
  - Is it possible to calculate via another state or prop?
5. How can you identify where state needs to live?
  - Identify a component a common parent that needs state, either this component or a component higher up should hold the state.

## Higher-Order Functions

From the Book [Eloquent JavaScript](https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK)

### Questions

1. What is a “higher-order function”?
  - They describe functions that operate on other functions giving a helpful abstraction.
2. Explore the `greaterThan` function as defined in the reading. In your own words, what is line 2 of this function doing?
  - Line 2 is returning a function that returns true or false on whether the argument of the new function is larger than the argument in the original function. This allows us on line 4 to define a new function that can test specifically for whether a number is larger than 10. You could also use greaterThan(n) to create other functions for testing other numbers.
3. Explain how either `map` or `reduce` operates, with regards to higher-order functions.
  - Map is also a higher-order function but instead of returning a function it takes a function as a parameter. The supplied function as an argument that can operate on each value in an array that map() is called on and returns a new array.

## Things I want to know more about

- Applying the single responsibility principle.
- Pulling JSON from APIs to populate a React app.


