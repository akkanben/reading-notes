# Reading Notes 09 - Forms and JS Events

## Forms

The `<form>` element holds all the elements that are related to the form. The "action" property points to the location of the page that will receive the data in the from. The "method" property controls the way the form is submitted, often "get" or "post".

The "get" method appends the values from the user in the address with a `?` separator. The "post" method is more secure and keeps the data in HTML headers.

The `<input>` tag used the "type" property to control which sort of input will be displayed for the user to interact with. Typically forms get submitted with a button or a textbox and contact a server, preform some operation with the data and give some kind of feedback.



### Input/Select/Option Types:

- `<input type="text">` & `<input type="password">`
  - "name"
  - "size"
  - "maxlength"
- `<input type="textarea">`
- `<input type="radio">` & `<input type="checkbox">`
  - "name"
  - "value"
  - "checked"
- `<input type="file">`
- `<input type="submit">`
  - "name"
  - "value"
- `<input type="image">`
- `<input type="hidden">`
- `<input type="date">`
- `<input type="email">`
- `<input type="url">`
- `<input type="search">`
  - "placeholder"
- `<select size="3">` Creates multiple selector.
- `<select multiple="multiple">` Allows multiple selections.
- `<select name="">`
- `<option>`
  - "value"
  - "selected"
- `<button>`
- `<label>` 
  - "for"
- `<fieldset>` Used to group form elements.
- `<legend>` Used directly after `<fieldset>` to identify the group of controls.

## Lists, Tables and more Forms

### Lists

- `list-style-type`
  - UL
    - "none"
    - "disc"
    - "circle"
    - "square"
  - OL
    - "decimal"
    - "decimal-leading-zero"
    - "lower-alpha"
    - "lower-roman"
    - "upper-roman"
- `list-style-image`
- `list-style-position`
  - "outside"
  - "inside"
- `list-style` Shorthand for style/image/position in any order.

### Tables

- `empty-cells`
  - "show"
  - "hide"
  - "inherit"
- `border-spacing`
- `border-collapse`

### Forms

- `cursor`
  - "auto"
  - "crosshair"
  - "default"
  - "pointer"
  - "move"
  - "text"
  - "wait"
  - "help"
  - "url('cursor.gif')"

## JS Events

HTML event handlers are considered bad practice, event listeners are the up to date way to handle events. Traditional DOM handlers (GlobalEventHandlers) are also available but their main limitation is that they can only attach a single function to any event.

The GlobalEventHandlers names start with the "on" prefix and do not use camelcase e.g. "GlobalEventHandlers.onblur"

Event listeners can be attached to elements and they can deal with more than one function at a time.

| Type            | Event Name                  | Description
|-----------------|-----------------------------|-------------
| UI Event        | load                        | |
| UI Event        | unload                      | Page is unloading, usually new page requested.|
| UI Event        | error                       | |
| UI Event        | resize                      | Browser window resize.|
| UI Event        | scroll                      | |
| Keyboard Event  | keydown                     | |
| Keyboard Event  | keyup                       | |
| Keyboard Event  | keypress                    | |
| Mouse Event     | click                       | |
| Mouse Event     | dblclick                    | |
| Mouse Event     | mousedown                   | |
| Mouse Event     | mouseup                     | |
| Mouse Event     | mousemove                   | Not touchscreen.|
| Mouse Event     | mouseover                   | Not touchscreen.|
| Mouse Event     | mouseout                    | Not touchscreen.|
| Focus Event     | focus/focusin               | The element gains focus.|
| Focus Event     | blur/focusout               | The element loses focus.|
| Form Event      | input                       | |
| Form Event      | change                      | |
| Form Event      | submit                      | |
| Form Event      | reset                       | |
| Form Event      | cut                         | | 
| Form Event      | copy                        | |
| Form Event      | paste                       | |
| Form Event      | select                      | |
| Mutation Event  | DOMSubtreeModified          | Change to the document.|
| Mutation Event  | DOMNodeInserted             | Node inserted as direct child of another node.|
| Mutation Event  | DOMNodeRemoved              | Node removed from other node.|
| Mutation Event  | DOMNodeInsertedIntoDocument | Node inserted as descendent of another node.|
| Mutation Event  | DOMNodeRemovedFromDocumnt   | Node removed as descendent of another node.|
| HTML5 Event     | readyStateChange            | |
| HTML5 Event     | DOMContentLoaded            | |
| HTML5 Event     | hashchange                  | |
| BOM Event       | touchstart                  | |
| BOM Event       | touchend                    | |
| BOM Event       | touchmove                   | |
| BOM Event       | orientationchange           | |


Event listeners examples from Duckett Book:

```javascript
function checkUsername() {
  var elMsg = document.getElementById('feedback');
  if (this.value.length < 5) { 
    elMsg.textContent = 'Username must be 5 characters or more';
  } else { 
  }
}
var elUsername = document.getElementById('username');
// When it loses focus call checkUsername()
elUsername.addEventListener('blur', checkUsername, false);

```
With parameter (Duckett):
```javascript
var elUsername = document.getElementById('username');
var elMsg = document.getElementById('feedback');
function checkUsername(minLength) {
  if (elUsername.value.length < minLength) {
    // Set the error message
    elMsg.innerHTML = 'Username must be ' + minLength + ' characters or more';
  } else { 
    elMsg.innerHTML = ''; 
  }
}
elUsername.addEventListener('blur', function() { 
  checkUsername(5); 
}, false);
```

The boolean parameter at the end of the `addEventListener()` method controls the flow of the event. Setting this to false is often the default choice and sets the flow to event bubbling. Setting it to true gives the flow event capturing behavior. Event bubbling begins at the furthest branch of the DOM tree, the most specific triggered element and bubbles out to the document. With event capturing it flows in the opposite direction where the event begins with the document and flows to the more specific element.

Using the event object allows us to reference details about the event itself, like the location etc.

Duckett example with event object:
```javascript
function checkLength(e, minLength) {
  var el, elMsg;
  if (!e) { 
    e = window.event;
  }
  el = e.target || e.srcElement;
  elMsg = el.nextSibling;

  if (el.value.length < minLength) {
    elMsg.innerHTML = 'Username must be ' + minLength + ' characters or more';
  } else { 
    elMsg.innerHTML = ''; 
  }
}
var elUsername = document.getElementById('username');
if (elUsername.addEventListener) {
  elUsername.addEventListener('blur', function(e) {
    checkLength(e, 5); 
  }, false); 
} else { 
  elUsername.attachEvent('onblur', function(e) {
    checkLength(e, 5);
  });
}
```

Event object methods:
- `preventDefault()` removes the expected behavior from certain events like form submissions and following links.
- `stopPropagation()` stops the event from continuing to bubble up.
