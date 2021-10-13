# Reading Notes 04: HTML Link, JS Functions, and Intro to CSS Layout

## Links

Links create the connections for all of the pages of the internet. Link connect different pages of the same website as well as bridge the gap from sites being hosted on other computers around the world. Links can also move the browser view to another location on the same page, or even open an email app addressed to the specified recipient.

The `<a>` (absolute) is the element used to create links. The "href" attribute is used to define the destination of the link. The "href" can be written with an absolute or relative path and be pointing to an internal page or an external http. The content between inside the tag determines the click-able link text/image.

The value of the "href" attribute can use relative links to describe where the file is located. `../links` or `../../stuff/links` can be used to point to folders.

- `<a href="http://www.kernel.org">The Linux Kernel Archives</a>`
- Email link: `<a href="mailto:ben@email.com">email me</a>`
- Link made to open in new window `<a href="www.mozilla.com" target="_blank">`
- A link to another section of a page `<a href="http://mysite/index.html#kittens">`

## Layout

Positioning Schemes:
- Normal Flow
  - This is the default way that browsers treat elements.
  - Block elements stack.
  - `position: static;`
- Relative Positioning
  - `position: relative;`
  - Offset with top/bottom/left/right properties.
- Absolute Positioning
  - `position: absolute;`
  - The element is not in the normal flow
  - Location can be set with top/bottom/left/right properties.
- Fixed Positioning
  - `position: fixed;`
  - Stays in position like absolute but doesn't move even if scrolled.
- Overlapping Elements
  - `z-index` property can be used to control layering.
- Floating Elements
  - `float` property will allow other content to flow around it.
  - Can be set left/right.
- Clearing Float
  - `clear` property can be assigned to left/right/both/none
  - Removes a previously applied float.
- Parents of Floated Elements

Multiple style sheets
- In the CSS file `@import url("other.css")`
- In the HTML head element `link rel="stylesheet" type="text/css" href="css/styles.css"`

## Functions, Methods, and Objects

### Basic Function

Functions allow a great deal of organization and also allow consolidation and reusing of code. Functions can also abstract working code to make it easier to comprehend, especially when well named.


A simple function can be written with the function keyword. To use the function just call its name with open/close parenthesis.

```javascript
function itSaMe() {
  console.log('I\'m Mario!')
}
itSaMe();
```

Parameters & Arguments

Functions can be written with input in mind. A function can be created to take one or more parameters. These are comma separated names placed between the parenthesis in the function definition. When the function is used variables/data can be placed in the parenthesis to be used as arguments for the function. Results can be output from the function with `return`.

```javascript
function addTwoNumbers(a, b) {
  return a + b;
}
let sum = addTwoNumbers(1, 1);
```
Variables declared inside a function have a scope that is local to the function. A variable declared outside the function as a global variable can be used inside the function. Local variables can not be used outside their scope but they can be used to return values.

## 6 Reasons for Pair Programming

[Code Fellows Link](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)

1. Greater efficiency
2. Engaged collaboration
3. Learning from fellow students
4. Social skills
5. Job interview readiness
6. Work environment readiness
