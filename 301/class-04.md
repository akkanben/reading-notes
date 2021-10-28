# Reading Notes 04 - 

## Forms

From the [React Documentation](https://reactjs.org/docs/forms.html)

### Questions

1. What is a ‘Controlled Component’?
  - A controlled component is a form element whos state is controlled by React.
2. Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.
  - We should store the responses as soon as they enter them so we can have complete control over the component with React and not allow it to control it's own state.
3. How do we target what the user is entering if we have an event handler on an input field?
  - We use the `onChange` property on the component along with a function to change the state property with `setState`.

## Ternary Operator

Article from [Codeburst.io](https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff)

### Questions

1. Why would we use a ternary operator?
  - For simple if/else statements it can be shorter can cleaner.
2. Rewrite the following statement using a ternary statement:
```javascript
x === y ? console.log(true) : console.log(false);
```

## Extra Links

- [React Bootstrap - Forms](https://react-bootstrap.github.io/components/forms/)
- [React Docs - conditional rendering](https://reactjs.org/docs/conditional-rendering.html)

## Things I want to know more about

- More practice building forms.



