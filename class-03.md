# Reading Notes 03: HTML Lists, Control Flow with JS, and the CSS Box Model

## HTML Lists

List tags in HTML come in 3 types:

1. Ordered lists (like this list).
  - Uses the `<ol>` tag.
  - Use it when the order matters.
2. Unordered lists.
  - Use the `<ul>` tag.
  - Like this nested list.
  - Use it when the order of items doesn't matter.
3. Definition lists
  - Use the `<dl>` tag.
  - Used for defining terms.
  - Multiple terms can share the same definition vice versa.

For both ordered lists and unordered lists the `<li>` element is used for each item in the list. For definition lists, use the `<dt>` to identify the definition term and use the `<dd>` to identify the definition's definition.


##  HTML Boxes

Box Model:

```
 -----------------------------
|           margin            |
|  ---------border----------  |
| |         padding         | |
| |   --------------------  | |
| |  |    content box     | | |
| |   --------------------  | |
| --------------------------  |
 -----------------------------

```

CSS rules has an effect on the HTML element and configurable box around that element. Here are a few ways CSS can control the box that surrounds each elelement:

- Box Dimentions contol the size of the content box.
  - `width`
  - `height`
- Measurement Units (some from [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units))
  - `px` absolute unit, actual pixels on the screen.
  - `cm`, `mm`, `in`, `pc`, `pt` are also absolute units.
  - `em` relative unit, the font size of the element (when used with font properties it refers to the parent element).
  - `ex`, `ch`, `rem`, `lh`, `vw`, `vh`, `vmin`,`vmax` are other releative units.
  - `%` a percentage as it relates to the parent container.
  - `auto` size adjusts to fit the parent container.
- Limiting width/height controls minimum and maximum size the content box can be when a responsive page design is being used.
  - `min-width`
  - `max-width`
  - `min-height`
  - `max-height`
- Overflowing Content determines how content behaves when it can not fit inside its content box.
  - `overflow`
  - values: hidden, scroll
- Border Options
  - `border-width`
    - other named values include: thin, thick, medium.
  - `border-style`
    - named styles include: solid, dotted, dashed, double, groove, ridge, inset, outset, hidden/none
  - `border-color`
  - `border` (shorthand)
    - takes 3 values in order: width, style, color.
- `padding` controls the space around the content box and extends the background-color of the content.
- `margin` controls the outermost area of the element, the white space around the element. 
  - The margins from two items next to each other will collapse in such a way that their margins will overlap as if the largest of the two was pressed against the border of the neighbor.
- `display` 
  - values include: inline, block, inline-block, none;
- `visibility`
  - values include: hidden, true.
- `border-image` uses an image for the texture of the border.
  - 3 values in order: the url, how to slice, and the corner style (stretch, repeat, round).
- `box-shadow` adds a dropshadow
  - At least the first 2 values and a color: horizontal offset, vertical offset, blur distance, spread of shadow, color. 
- `border-radius` controls the sharpness of the corners of the border.
  - 4 values in order: top, right, bottom, left.
  - Individual corners can be selected: border-top-left-radius etc.

## More Decisions and Loops

### Switch

Switch statements control the flow by evaluating a variable in various cases and ending with a default case. Break statements are used to stop a case from falling to the next case and the default case is a catch all.

```javascript
switch(snack) {
  case 'apple':
    return 'healthy';
  case 'candy':
    return 'unhealthy';
  default:
    return 'that was something';
}
```

### Type Coercion and Weak Type

JavaScript tries to be helpfull and does some number type coercion when evaluating numbers as strings against actual numbers. Because of this JavaScriptis refered to as a weak typed language. This coercion applies to evaluating expressions and the strick equals/greater etc. apply to these.

### Truthy & Falsy

Like the way numbers and numbers as strings are coerced, true and false can be coerced as well.

Falsy
- `false`
- `0`
- `''`
- `NaN`
- `undefined`

Truthy is mostly anything else
- `true`
- `1` any number other than 0
- `'abc'` a non empty string

Logical operators like `||` and `&&` are evaluated left to right and as soon as enough information is known to determine the outcome it just returns right away without even checking the rest.

### For Loops

The 'for loop' has 3 parts inside its parenthesis separated by semicolons. The first part is a variable to be the counter, the second part is the condition that needs to evaluate true for the loop to continue, and the last part controls the way the the first part (counter) is changed i.e. incremented/decremented etc.

```javascript
for (let i = 99; i > 0; i--) {
  console.log('There are ' 
               + i + ' bottles of beer on the wall ' 
               + i + ' bottles of beer, take one down, pass it around ' 
               + (i - 1) + ' bottles of beer.')
}
```

### While Loops

While loops continue to execute until the expression in the parenthesis evaluates false. 

```javascript
let a = 5;
let b = 0;
while (a > b) {
  console.log("a is still bigger");
  b++;
}
console.log("oh hey, now that's not true anymore.");
```

'Do while' loops are similar to while loops except the body of the loop runs at least once even if the while expression is false from the jump.

```javascript
let potatoCount = 0
do {
  console.log('I\'m still going to say I\'ve got ' + potatoCount + ' potatoes.');
  // do math with potatoes
} while (count > 0)
```
