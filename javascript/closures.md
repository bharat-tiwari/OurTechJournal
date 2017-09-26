#Closure
In javascript, when a function is invoked 
 - an 'execution context' is created for the function
  - each 'execution context' has a 'variable environment' where the variables declared inside the function live

Often in your js code, you would need to define a function inside another function (maybe for data privacy, or for callback functions). The inner function may have to use a variable defined in the outer variable.

Below JS Fiddle demonstrates a simple closure:




[JsFiddle Example](https://jsfiddle.net/tiwarib/4gyrd707/#tabs=js,result,html)

#Pitfalls of using Closures




