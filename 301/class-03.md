# Reading Notes 03 - Passing Functions as Props

## React Docs: Lists and Keys

From the [React.js Documentation](https://reactjs.org/docs/lists-and-keys.html)

### Questions:

1. What does .map() return?
  - The `.map()` method iterates over each item in the array it is called on returns a new array built from the callback function.
2. If I want to loop through an array and display each value in JSX, how do I do that in React?
  - As you iterate the array you could return each element inside JSX curly braces nested in a react component.
3. Each list item needs a unique ...
  - Key
4. What is the purpose of a key?
  - The key will make sure each element is easily identifiable to React helping out when React needs to update a specific element with siblings.

## The Spread Operator

From the [Coding at Dawn Medium article](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab)

### Questions:

1. What is the spread operator?
  - It is a tool for expanding an array that can be used as a shortcut for many common tasks.
2. List 4 things that the spread operator can do.
  - Allows you to spread out an array into the arguments of a function.
  - Concatenate two arrays or copy an array's contents.
  - Combining objects.
  - Splitting strings into individual charactors as elements of an array.
3. Give an example of using the spread operator to combine two arrays.
```javascript
const alpha = ['a', 'b', 'c'];
const bet = ['d', 'e', 'f'];
const alphabet = [...alpha,...bet]; // ['a', 'b', 'c', 'd', 'e', 'f'];
```
4. Give an example of using the spread operator to add a new item to an array.
```javascript
const oneMoreLetter = [...alphabet,'g']; //  ['a', 'b', 'c', 'd', 'e', 'f', 'g'];
```
5. Give an example of using the spread operator to combine two objects into one.
```javascript
const veg = {tomatoCount: 1, cucumberCount: 2};
const moreVeg = {lettuceHeadCount: 1};
const salad = {...veg, ...moreVeg} // {tomatoCount: 1, cucumberCount: 2, lettuceHeadCount: 1} 
```

## How to Pass Functions Betwen Components

From the [Steve Griffith YouTube video](https://www.youtube.com/watch?v=c05OL7XbwXU)

### Questions:

1. In the video, what is the first step that the developer does to pass functions between components?
  - The developer creates a method in the App class that will be then passed to the child Person class.
2. In your own words, what does the increment function do?
  - The increment method in the Person class adds a yellow span to the card and calls the App class increment method which filters out the current name and increments it's corrosponding count. 
3. How can you pass a method from a parent component into a child component?
  -  As a property in the React component just like passing any other property via props.
4. How does the child component invoke a method that was passed to it from a parent component?
  - Using `this.props` and the property sent to it from the parent component.

## Additional Links

- [React Tutorial through ‘Declaring a Winner’](https://reactjs.org/tutorial/tutorial.html)
- [React Docs - Lifting State Up](https://reactjs.org/docs/lifting-state-up.html)
