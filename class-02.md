# Reading Notes 02: Basics of HTML, CSS & JS

## HTML Text

Structural Markup examples:
- `<b>` make text appear **bold**.
- `<i>` make text appear *italic*.
- `<sup>` give a superscript like x<sup>3</sup>.
- `<sub>` give a subscript like C<sub>7</sub>H<sub>12</sub>O<sub>6</sub>.
- Others Mentions:
  - Whitespace can make it easier to read code but it will collapse, the element will control the newlines.
  - `<br />` will add a new line.
  - `<hr />` will create a horizontal rule

Semantic markup elements are used to apply added meaning to the page, examples:
- `<strong>` will indicate the word has a strong importance and may be heard when read.
- `<em>` will indicate emphasis on the content inside will change the meaning of the content.
- `<blockquote>` indicates the content is a quotation.
- `<q>` indicates the content is a quotation.
- `<abbr>` indicates abbreviation and when used with the 'title' attribute the full meaning can be specified.
- `<cite>` indicates the content is a book/film/paper etc.
- `<dfn>` indicates the enclosed term is being defined for the first time.
- `<address>` is used for contact details for the author of the page.
- `<ins>` is used to clarify the enclosed content has been inserted after the initial publication.
- `<del>` indicates the content has been been removed.
- `<s>` indicates the content is no longer accurate or relevant.

## CSS

CSS rules are used to style the elements on the page. HTML elements have default values but CSS can be used to freely change them. CSS styling can be applied directly to an element by using a style attribute but typically if they inside the HTML document they are placed in a `<style>` tag.

CSS rules are organized by selectors and property/value pairs. Each property/value pair is separated by a semicolon and wrapped in curly braces. There can be one or more selectors separated by commas.

Internal CSS:

```html
<style>
  p, h2 {
    color: red;
    font-size: 15pt;
  }
</style>
```

Separate files can be used for CSS with the same syntax (minus the style tags). To connect with an external CSS style-sheet just add the appropriate `<link>` element inside the `<head>` of the HTML document:

`<link href="css/styles.css" type="text/css" rel="stylesheet" />`

### CSS Selectors Cascading and Inheritance

| Selector Name             | Explanation                                       | Selector        |
|---------------------------|---------------------------------------------------|-----------------|
| Universal Selector        | Selects Everything                                | `* {}`          |
| Type Selector             | Selects all `<h1>`'s and `<h2>`'s                 | `h1, h2 {}`     |
| Class Selector            | Selects any element with "class=rad"              | `.rad {}`       |
| Class Selector            | Selects any `<a>` element with "class=rad"        | `a.rad {}`      |
| ID Selector               | Selects the element with "id=123"                 | `#123 {}`       |
| Child Selector            | Selects any `<img>` that is a child of `<header>` | `header>img {}` |
| Descendant Selector       | Selects any `<a>` that is a descendant of `<p>`   | `p a {}`        |
| Adjacent Sibling Selector | Selects the first `<ul>` after the `<p>`          | `p+ul {}`       |
| General Sibling Selector  | Selects any `<p>` that is a sibling of `<header>` | `header~p {}`   |

It's possible to end up selecting an element in more than one way. In these cases there is a cascading effect and if the selectors are equal then the selector that is lower down in the document will take priority. Additionally if a selector is more specific in its selection then it will take priority. 

A "universal selector" is less specific than a "type selector" is less specific than more than one "type selectors" is less specific than a "class selector" is less specific than an "ID selector" and so on ... Look at (https://cssspecificity.com) for a good infographic.

Certain element properties can be inherited by their descendants. According to the [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance) "Which properties are inherited by default and which aren't is largely down to common sense." There are a few property values that can help control inheritance:

- "inherit" sets the value to be the same as the parent.
- "initial" sets it back to it's initial/default state.
- "unset" sets the element's inheritance back to it's default behavior.

## JS

### Basic JavaScript Instructions

JavaScript is one or more statements. Each statement ends with a semicolon. 

Comments are lines in the code that are ignored by the browser, their purpose is to clarify code to make it easier to read for other or for future you. In JavaScript comments can be written 2 ways: single lines that start with `//` or blocks of text that can span multiple lines beginning with `/*` and ending with `*/`.

```javascript
/* 
 * Favorite
 * Things
/*

let favoriteNumber = 7;
let favoriteMeal = 'spaghetti';
// Change meal here
meal = 'yakisoba'; 
```

### Data Types

- Number `let lilPI = 3.14;`
- String `let garment = 'Michelle\'s dress';`
- Boolean `let sleepy = true;`
- Array `let fruits = ['apple', 'orange', 'banana']`

Rules for variable names:

1. First letter can not be a number. It must begin with a letter a dollar sign or an underscrore.
2. Must not contain a dash or a period.
3. Can not use a keyword that is defined in the JavaScript language.
4. JavaScript is case-sensitive and so are variables.
5. Use a good descriptive name that makes sense for the data it holds or the way it's being used.
6. Multiword variable names are great just use camelCase.

### Changing Variables

The value in a variable can ... vary. Variables and be combined with other variables, they can have operations done on them generally get changed all around. Example:

```javascript
let consoles = ['atari', 'nes', 'sms', 'snes', 'genesis'];
let favGame = 'Super Mario Bros.'
let message = 'My first console was an ' + consoles[1] + ' and I loved ' + favGame;
let currentYear = 2021;
let SMByear = 1990;
favGame = 'Super Mario World';
let diff = currentYear - SMByear;
console.log(favGame + ' came out ' + diff + ' years ago.');

```

| Sign | Operator Name  | Type       |
|------|----------------|------------|
| \+   | Addition       | Arithmetic |
| \-   | Subtraction    | Arithmetic |
| /    | Division       | Arithmetic |
| \*   | Multiplication | Arithmetic |
| ++   | Increment      | Arithmetic |
| \-\- | Decrement      | Arithmetic |
| %    | Modulus        | Arithmetic |
| \+   | Concatenation  | String     |
| \=   | Assignment     | Assignment |

### Decisions and Loops

Conditionals are tests that can control the flow of the code.

| Conditional | Description              |
|-------------|--------------------------|
| ==          | is equal to              |
| ===         | strict equal to          | 
| !=          | not equal to             |
| !==         | strict not equal to      |
| \>          | greater than             |
| \<          | less than                |
| \>=         | greater than or equal to |
| \<=         | less than or equal to    |

Logical Operators work with conditionals to make more complex tests.

| Logical | Description |
|---------|-------------|
| &&      | Logical AND |
| \|\|    | Logical OR  |
| !       | Logical NOT |

If statements will only run a section of code between curly braces if the condition in the parenthesis is true. Else statment are an optional extention to if statements that will designate the code to run if the conditional in the if is false.

```javascript
let walletBalance = 12.00;
let pizzaSlice = 7.50;
if (walletBalance - pizzaSlice >= pizzaSlice) {
  console.log("Yay, I can afford another slice!")
} else {
  console.log("Sad Panda...")
}
```


## Git-Commit

Notes from [Chris Beams's Article](https://chris.beams.io/posts/git-commit/)

Commit messages should communicate the context of the change. Teams should come up with a standard and stick to it. Avoid guesswork and make logs easier to read by spelling out words and using markup syntax.

7 Rules:

1. For longer commits use a blank line to separate the subject from the body.
2. No more than 50 characters for the subject.
3. Capitalize the subject line.
4. No periods to end the subject line.
5. Imperative mood in subject line.
6. Wrap at 72 characters.
7. Body should be used for the "what" and "why" instead of the "how".

Strive for atomic commits and commit more often! To help with the imerative voice imagine adding "If applied, this commit will `<insert commit>`".
