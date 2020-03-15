# Execution Context

In Javascript, whenever a code starts running/execution, an **Execution Context** is created. Its that logical wrapper inside which the code executes. 

At the very first, Global Execution Context is created, in which the globally declared variables and functions are placed and global code is executed. 

\(In javascript, any code that is not inside a function is global.\)

Once any function is called in the global code, an inner Execution context is created for the called function 

When the base Global Execution Context is created, the Javascript engine automatically creates three things for us:

* **Global** object \(in case of Browsers, the window object points to this Global object\)
* **'this'** variable  - in Global context, 'this' points to the Global object and thus to window object
* a link to outer environment \(in case of Global execution context, the outer environment would be null or undefined as Global context is the outermost context one can get to\)

