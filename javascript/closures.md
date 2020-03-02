# Closures

## Closure

Often in your js code, you would need to define a function inside another function \(maybe for data privacy, or for callback functions\). The inner function may have to use a variable defined in the outer variable.

In javascript, when a function is invoked

* an **'execution context'** is created for the function
  * each 'execution context' has a **'variable environment'** where the variables declared inside the function live

When the function completes and returns back, its execution context no longer exists and the variables in the context would usually be eventually cleaned up by the garbage collector.

However, when a function has another inner function defined inside it, its variables remain persisted, not cleaned up by the garbage collector even after the outer function completes and returns and its execution context no longer exists.

Lets imagine, after calling the outer function, at some later point of time in the application code, the inner function is called/invoked. This would create a new execution context for the inner function. Even though the execution-context of outer function doesn't exist at this time, the inner function can continue to use the variables and their values defined in the outer function as those variables still exist in the memory.

Below JS Fiddle demonstrates a simple closure. In the below js code, the function `paymentService` defines a variable `currency` and calculates its value based on the `country` parameter passed to it. It then returns back another inner anonymous function which accepts `amount` parameter and returns a the formatted amount string using the `currency` variable that was calculated in the outer function. JS Closure allow this inner function to use the `currency` variable from outer function even though the 'execution context' of the outer function no longer exists at the time when inner function is invoked.

[JsFiddle Example](https://jsfiddle.net/tiwarib/4gyrd707/#tabs=js,result,html)

## Pitfalls of using Closures

