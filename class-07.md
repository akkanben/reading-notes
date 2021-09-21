# Reading Notes 07 - Object-Oriented Programming, HTML Tables

## Domain Modeling

from [Domain Modeling (Code Fellows Git)](https://github.com/codefellows/domain_modeling#domain-modeling)

A Domain model is tool for simulating a model for a problem with behavior and data. 

An example from the article using a function expression constructor and a method with the constructor functions prototype:
```javascript
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}
EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
EpicFailVideo.prototype.dailyLikes = function() {
  var viewers, percentage;
  viewers = this.generateRandom(10, 30) * this.epicRating;
  if (this.hasAnimals) {
    percentage = 0.75;
  } else {
    percentage = 0.40;
  }
  return Math.round(viewers * percentage);
}
var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);
console.log(parkourFail.dailyLikes());
console.log(corgiFail.dailyLikes());

```
Objects that share prototypes, share the same code and consume less memory. Even though it is slower to execute, it is considered a best practice.


## HTML Tables

The `<table>` element holds an HTML table and the `<tr>` is used for each row. Rows are filled with data and the number of `<td>` elements used will determine how many columns are in the table. The `<th>` can be used in place of a `<tr>` when a table header is desired.

The cells in rows and columns can be connected if a larger cell is desired. `colspan` can be used on the specific `<td>` to extend it. For larger tables `<thead>`, `<tbody>`, and `<tfoot>` can be used to organize. The table header and footer can also be made to display in situations when the data extends past the screen.

## Functions, Methods, and Objects continued.

Another way to create an object in JavaScript is with the `new` keyword and the `Object()` function.

```javascript
// Constructor notation
let myObject01 = new Object();
myObject01.name = 'Thing One';
// Literal notation
let myObject02 = {};
myObject02.name = 'Thing Two';

```

We can define a special contractor function to define a template to be used to instantiate more objects with the `new` keyword.

```javascript
// Constructor function
function Hero(name, class, hp) {
  this.name = name;
  this.class = class;
  this.hp = hp;
  this.speak = function() {
    return 'Greetings, I\'m '+ this.name + ' .';
  }
}

let hero01 = new Hero('Doug', 'Cleric', 10);
let hero02 = new Hero('Jasmine', 'Warrior', 30);
```

The `this` keyword has a different meaning depending on where it is declared. At the global scope it is in reference to the window object as in `this.innerWidth`. When `this` is used inside an object is reference the object itself.

### JavaScript Built-in Objects

#### The Browser Object Model refers to the browser window/tab.

Properties
- `window.innerHeight`: Widow height.
- `window.innerWidth`: Widow width.
- `window.pageXOffset`: Horizontal scroll distance.
- `window.pageYOffset`: Vertical scroll distance.
- `window.screenX`: X position of pointer from top-left corner of screen.
- `window.screenY`: Y position of pointer from top-left corner of screen.
- `window.location`: Current URL
- `window.document`: Reference to current page.
- `window.history`: Reference to viewed pages.
- `window.history.length`: Number of history items.
- `window.screen`: Reference to screen object (computer monitor).
- `window.screen.width`: Screen (monitor) width.
- `window.screen.height`: Screen (monitor) height

Methods
- `window.alert()`: A popup with OK.
- `window.open()`: Opens a URL in a new window (may be blocked by browser)
- `window.print()`: Acts like pressing print from browser UI.

#### The Document Object Model

Properties
- `document.title`: Title of current document.
- `document.lastModified`: Date last modified.
- `document.URL`: Current url.
- `document.domain`: Returns domain name.

Methods
- `document.write()`: 
- `document.getElementById()`: 
- `document.querySelectorAll()`: 
- `document.createElement()`: 
- `document.createTextnode()`: 

#### Global Objects

String Properties
- `length`

String Methods
- `toUpperCase()`
- `toLowerCase()`
- `charAt()`
- `indexOf()`
- `lastIndexOf()`
- `substring()`
- `split()`
- `trim()`
- `replace()`

Number Methods
- `isNaN()`
- `toFixed()`: Rounds to specified decimal place.
- `toPrecision()`: Rounds to specified number of digits.
- `toExponential()`: To scientific notation.

Math Properties
- `Math.PI`

Math Methods
- `Math.round()` Round to nearest integer
- `Math.sqrt(n)`
- `Math.ceil()`: Round up to nearest integer.
- `Math.floor()`: Round down to nearest integer
- `Math.random()`

Date Methods
- `getDate()` & `setDate()`
- `getDay()`
- `getFullYear()` & `setFullYear()`
- `getHours()` & `setHours()`
- `getMilliseconds()` & `setMilliseconds()`
- `getMinutes()` & `setMinutes()`
- `getMonths()` & `setMonths()`
- `getSeconds()` & `setSeconds()`
- `getTime()` & `setTime()`
- `getTimezoneOffset()`
- `toDateString()`
- `toTimeString()`
- `toString()`

