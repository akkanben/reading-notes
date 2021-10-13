# Reading Notes 01 - Introduction to React and Components

## Component-Bases Architecture

Article from [Tutorials Point](https://www.tutorialspoint.com/software_architecture_design/component_based_architecture.htmu).

### What is a “component”?

When using component based architecture, a component is a building block, a reusable chunk of code that encapsulates a set of related functions.

### What are the characteristics of a component?

1. Components are typically designed to be reused.
2. Components can be substituted with other, similar components.
3. Components are designed to work in a variety of environments and contexts.
4. Components can be extended to allow for new features or behaviors.
5. Components hide their details and encapsulate their internal variables, states, and processes.
6. Components are designed to be independent, typically designed with none or few dependencies.

### What are the advantages of using component-based architecture?

Component-bases architectures can be easier to deploy because swapping components shouldn't impact other components. Costs can be cut by using third-party components and reducing development and maintenance. Since components are well defined combining them to create an app doesn't impact the system itself or other components making development easier. Components are reusable thereby speeding up and reducing costs to development. Components reduce technical complexity by allowing for abstraction via component containers/services. The reliability increases because of the reuse of components. Components are independent and this allows for groups to work in parallel increasing productivity.

## What is Props and How to Use it in React

Article from [IT Next](https://itnext.io/what-is-props-and-how-to-use-it-in-react-da307f500da0#:~:text=%E2%80%9CProps%E2%80%9D%20is%20a%20special%20keyword,way%20from%20parent%20to%20child)

### What is “props” short for?

The keyword `props` is short for properties.

### How are props used in React?

React's `props` is used to pass properties from component to component. The data in `props` is immutable.

### What is the flow of props?

The `props` flow from top to bottom or parent to child, in one direction.


## Other Readings from React.js Documentation

- [React Tutorial through ‘Passing Data Through Props’](https://reactjs.org/tutorial/tutorial.html)
- [React Docs - Hello world](https://reactjs.org/docs/hello-world.html)
- [React Docs - Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
- [React Docs - Rendering elements](https://reactjs.org/docs/rendering-elements.html)
- [React Docs - Components and props](https://reactjs.org/docs/components-and-props.html)

## Things I want to know more about

- Object oriented programming design patterns
- What other settings can React be used in aside from the browser via ReactDOM? 
- JSX
- Organizing React apps with more than one src file.
- How ReactDOM determines what has changed for DOM updates.
