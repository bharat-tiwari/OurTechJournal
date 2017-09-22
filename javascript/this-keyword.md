# 'this' keyword
In javascript, when a function is invoked 
 - an 'execution context' is created for the function
  - each 'execution context' has a 'variable environment' where the variables declared inside the function live
  - the 'execution context' has a reference to its 'outer environment'
  - if the function code uses a variable which is not declared inside the function, then it can look for it in its 'outer environment'. If that 'outer environment' is another parent function and doesn't have the variable, the code can look for the variable further next level of outer environment until it reaches the global environment. 
  
 - Every time javascript creates an 'execution context', it automatically creates a variable called **'this'**. 
  
  **'this' **could be pointing to different objects depending on how the function has been invoked.
  
  
  1. When used in global scope, `this` points to `window` object
  2. When used inside a function statement or expression defined in global scope, `this` points to `window` object
  3. When used in a function defined inside an object - `this` points to the  object
  4. When used in a function nested inside a function defined inside an object - `this` points to `window` object. This is little weird. As a workaround for this, many developers define another variable usually named `that` or `self` in the parent function and assign it to `this`. Then use `that`/`self` in the nested function instead of `this`.
  

  


  