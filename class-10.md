# Reading Notes 10 - Debugging


## Error Handling and Debugging

Grace Hopper coined the 'bug' in debugging after removing a moth caught in a relay inside the Harvard Mark II. Nowadays bugs are known as defects or problems that prevent the intended outcome of a program. There are many causes for a bug but according to [wikipedia](https://en.wikipedia.org/wiki/Software_bug#Types) some of the types include conceptual error, arithmetic, logic, syntax, resources, multi-threading, interfacing, and teamwork.

### Execution

Understanding the flow of the program and the order that commands are executed will make sure you are searching for the bug in the correct place. The JavaScript interpreter works through the code line by line and if it comes to a function it takes care of that before continuing, this is the case for nested functions as well. Each task is added to the stack of tasks. The scope of functions and variables is also very important to consider when working out where your bug is coming from.

Although JavaScript interprets the code line by line, declarations are put into memory before it executes any code. Because of this it is possible to assign the definition of a variable or function further down in the document than the actual call.

### Errors

Error objects contain a "name" that lets you know the type of error; "message" that gives information; "fileNumber" that references the file name in question; "lineNumber" the particular line the error discovered.

| Error Type | Description |
|------------|-------------|
| Error      | Generic     |
| EvalError  | related to global function `eval()`|
| RangeError | Numeric value outside valid range |
| ReferenceError | Invalid reference i.e. not declared/in scope |
| SyntaxError | Incorrect coding grammar |
| TypeError | When data type is not valid or can not be coerced |
| URIError | `encodeURI()` or `decodeURI()` was passed invalid data |
| AggregateError | When multiple errors need to be reported as in `Promise.any()` |
| InternalError | Internal error in JavaScript engine, e.g. "too much recursion" |

### Debugging Workflow

When there are errors you can control track them down and make changes. When there is a chance for error that is out of your control use "try", "catch", "throw", and "finally" to handle them gracefully.

Tracking Down a Bug:

Where:
1. Carefully check the error details and look at the location in the script the interpreter is pointing to.
2. Determine how far the script gets before the error.
3. Use breakpoints to stop the flow of code and checkout variable values at a specific time.

What:
1. Using breakpoint check whether variables have the expected values
2. Test smaller chunks of code alone.
3. Check to confirm the correct number of values in an array or arguments in a function.

#### Console Log

The `console.log` command can run in three different modes that use colors/icons to distinguish: `console.info()`, `console.warn()`, and `console.error`.

It is also possible to group logs together by logging between `console.group()` and `console.groupEnd()`. Objects and arrays can be logged as a table as well with `console.table()`.

### Breakpoints

After marking breakpoints in the browser developer tools you can run the script step by step choosing to skip over function calls or follow them.

Breakpoints can also be made directly in the script by using the `debugger` command.

### Exceptions

The error handling keyword `try{}` can be used to surround the code that may fail (usually due to user interaction). If something in the `try` block throws an exception then the following `catch{}` offers alternate code to use. The `finally{}` block will run either way, this runs even if the try/catch has a return.

