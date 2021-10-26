# Reading Notes 02 - State and Props


## React Lifecycle

From the article [React lifecycle](https://medium.com/@joshuablankenshipnola/react-component-lifecycle-events-cb77e670a093)

### Questions:

1. Based off the diagram, what happens first, the ‘render’ or the ‘componentDidMount’?
  - The initial `render` will happen before the `componentDidMount`
2. What is the very first thing to happen in the lifecycle of React?
  - The `constructor` is the very first thing to happen in the lifecycle.
3. Put the following things in the order that they happen: componentDidMount, render, constructor, componentWillUnmount, React Updates
  - In order those items would be:
    1. constructor
    2. render
    3. componentDidMount
    4. React Updates
    5. componentWillUnmount
4. What does componentDidMount do?
  - It lets you place code that can be assued that the component is already in the DOM and can be used.


## React State Vs Props

From the video [React State Vs. Props](https://www.youtube.com/watch?v=IYvD9oBCuJI)

### Questions:


1. What types of things can you pass in the props?
  - You can pass anything that that would be an argument to a function: numbers, strings, objects, arrays etc.
2. What is the big difference between props and state?
  - State is private and controlled internally by the component whereas props are passed into the component and are immutable once passed in.
3. When do we re-render our application?
  - React will re-render whenever there is a state change. Usually we re-render our application based off user interactions but something like setInterval() could also be used to change the state.
4. What are some examples of things that we could store in state?
  - State can store things that are handled inside the component like timers, or various form input elements.

## Other Links

- [React Bootstrap Documentation](https://react-bootstrap.github.io/)
- [Netlify](React Tutorial through ‘Developer Tools’)
- [React Docs - State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- [React Docs - handling events](https://reactjs.org/docs/handling-events.html)
- [React Tutorial through ‘Developer Tools’](https://reactjs.org/tutorial/tutorial.html)

## Things I want to know more about

- Why there are so many [different syntax options](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import?retiredLocale=pt-PT) to import things?
- How bigger React apps are organized and what they look like.
- Netlify
- React Bootstrap
