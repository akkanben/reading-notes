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


Example using props from the article:

```
const ChildComponent = (props) => {  
  return <p>{props.text}</p>; 
};

class ParentComponent extends Component {  
  render() {
    return (
      <h1>
        I'm the parent component.
        <ChildComponent text={"I'm the 1st child"} />
        <ChildComponent text={"I'm the 2nd child"} />
        <ChildComponent text={"I'm the 3rd child"} />
      </h1>
    );
  }
}
```


## Other Readings from React.js Documentation

### [React Tutorial through ‘Passing Data Through Props’](https://reactjs.org/tutorial/tutorial.html)

### [React Docs - Hello world](https://reactjs.org/docs/hello-world.html)

From the Docs:
```js
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```

### [React Docs - Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

JSX looks like HTMl. JSX is used to describe elements. We can wrap any valid JavaScript inside curly braces. Multiline JSX should be wrapped in parenthesis to avoid automatic semicolon insertion.

From the Docs:

```js
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

### [React Docs - Rendering elements](https://reactjs.org/docs/rendering-elements.html)

Using the `ReactDOM.render()` function we can render an element to an existing element on the DOM. React elements are immutable so they can not be changed but they can be replaced. React is also smart about how it updates the DOM, only updating the parts that are actually changing.

Docs ticking-clock example only updates the date text each 1000ms:

```js
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));}

setInterval(tick, 1000);
```

### [React Docs - Components and props](https://reactjs.org/docs/components-and-props.html)

Separating components into smaller components can be a good strategy designing apps. It allows for sections of code to be better resued. This example below shows a before and after from the Reactjs docs of splitting up a component:

Before:

```js
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```
After:

```js
function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />
  );
}

function UserInfo(props) {
  return (
    <div className="UserInfo">
      <Avatar user={props.user} />
      <div className="UserInfo-name">
        {props.user.name}
      </div>
    </div>
  );
}

function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}

```

## Things I want to know more about

- Object oriented programming design patterns
- What other settings can React be used in aside from the browser via ReactDOM? 
- JSX
- Organizing React apps with more than one src file.
- How ReactDOM determines what has changed for DOM updates.
