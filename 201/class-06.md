# Reading Notes 06: Problem Domain, Objects, and the DOM

## Problem Domain 

From [Understanding The Problem Domain Is The Hardest Part Of Programming](https://simpleprogrammer.com/understanding-the-problem-domain-is-the-hardest-part-of-programming/)

Much of the difficulty in programming stems from a less than complete understanding of the problem you are trying to solve. Learning new technologies can be much easier if you practice them in the context of a known problem domain.

## Primitives vs. Objects

From [What's the Difference Between Primitive Values and object References?](https://betterprogramming.pub/intermediate-javascript-whats-the-difference-between-primitive-values-and-object-references-e863d70677b)

### Data Types and Mutability

Boolean, Null, Undefined, Number, BigInt, String, and Symbol are all JavaScript primitive types and are all immutable. Objects are the eighth data type and are mutable. Objects are also the underlying foundation for arrays, functions, and date types. 

Immutable types can not be changed. There are functions like `String.slice(0, 8)` that seem to change but in truth they are just returning a new string and reassigning the new value. This is why `myString[1] = 'a'` results in an error, the string is immutable.

Objects, however can be changed and if you try to reassigning them like you might do to a string, you'll find that the original object is just referenced twice with both reflecting the latest change. `Object.assign()` can be used to create a new object when that is the desired functionality.

### Comparison Operators

Because objects do not contain values directly (only references to values) even objects with the same contents will not evaluate as equal. To compare objects you must compare their content something like `JSON.stringify(myObject01) === JSON.stringify(myObject02)` would evaluate to true if the object's contents were the same.

## Object Literals

Object literals can be created directly using literal notation, much like the way arrays can be created with data already inside. Objects can house properties and methods (functions) and these can be accessed with dot notation or square brackets.

```javascript
let hero = {
  'name': 'Kirby',
  'strength': 11,
  'dexterity': 14,
  'constitution': 10,
  'intelligence': 4,
  'wisdom': 13,
  'charisma': 17,
  'favFoods': ['carrots', 'peanuts', 'pizza'],
  greeting: function() {
    return `Hi I'm ${this.name}.`;
  }
};

hero.greeting(); // outputs "Hi I'm Kirby."
console.log(hero['strength']); // outputs 11
console.log(hero.wisdom); // outputs 13
```

## Document Object Model, the DOM

The DOM is a tree (as defined in discrete mathematics) shaped collection of nodes that is stored in the browsers memory. There are four types of nodes:

- Document Node: represents the html document itself, all other nodes stem from this node.
- Element Node: describes the structure of the HTML page. Basically all the tags/elements.
- Attribute Node: describes the attributes that may exist on elements.
- Text Node: A child of an element, this is the text content itself. Text nodes can not have children.

### Accessing the DOM and Using Elements

Methods for Returning Elements:
- Single Selection: returns a single node.
  - `getElementById()`
    - Select by the element's ID
    - `getElementById('001')`
  - `querySelector()`
    - Use CSS selectors to return the first matching node.
    - `querySelector(article:last-child)`
- Multiple Section: Returns a node list.
  - `getElemetnsByClassName()`
    - Matches a class name.
    - `getElemetnsByClassName('myClass')`
  - `getElementsByTagName()`
    - Matches a specific tat.
    - `getElementsByTagName(li)`
  - `querySelectorAll()`
    - Use CSS selectors to return all matches.
    - `querySelectorAll('article.bio')`
- Traversing i.e. `getElementById('001').parentNode`
  - `parentNode`
  - `previousSibling`/ `nextSibling`
  - `firstChild` / `lastChild`

Node lists can be iterated and selected by index like arrays with square brackets or by the item() function, their length can similarly be returned with `.length`. Selected elements can be stored in a variable or processed immediately. 

Text nodes can be worked with directly with the `nodeValue` property, or their parent node can be selected and the containing element can be retrieved or updated with:

- `innerHTML` Good for updating larger sections, DOM manipulation is better suited for individual nodes as it is a bit slower.
- `textContent` Doesn't return any markup within the element.
- `innerText` is to be avoided in general due to poorer performance, if hidden by CSS will not return on a query. 

There are security issues to be understood when using `innerHTML`. Do not use HTML from untrusted sources or from user input. There are simple ways attackers can run their own scrips and cause all kinds of problems. Additionally when taking user input only needed characters should be accepted and any data from untrusted sources should be escaped on the server before it is shown on the page. 

Don't put user content here:
- Inside script tags.
- Inside HTML comments.
- Tag names.
- Attributes.
- CSS values.

DOM elements can be created with `createElement()` and `createTextNode()`. The new elements and be attached to another element with `appendChild()`. Dom elements can also be removed from the tree with `removeChild()`, to achieve this store both the parent and child in a variable and then preform `parentEL.removeChild(elementToRemove)`. 

Attribute nodes have several methods:
- `getAttribute()`
- `hasAttribute()`
- `setAttribute()`
- `removeAttribute()`



