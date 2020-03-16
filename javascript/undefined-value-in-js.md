# undefined value in JS

In Javascript, `undefined` does not mean some empty value or undeclared variable.

If a variable has a value `undefined`, it means it has been declared in the code, it has been hoisted in the memory space/execution context but has not been assigned any value. Thus `undefined` is a special value in javascript, all variables declared in the code are assigned this undefined value in the 1st phase of code execution cycle. \( Javascript code is executed in two phases - see Javascript Code Execution topic\).

If your code uses some _undeclared_ value, the javascript execution will throw an error `'Uncaught Reference Error: <<var>> is not declared'`

Since `undefined` is a special variable/value in javascript, we can write boolean expressions comparing a variable to `undefined`.

```text
console.log(a)

/// ------- output
/// above code would trigger an error when the code runs
/// Uncaught Reference Error: a is not declared
```

```text
var a;
console.log('>>>>', a)

if (a === undefined) {
 console.log('>>>> a has a value of undefined');
} else {
 console.log('>>>> a has some defined value');
}

/// ------- output
/// above code would output below
/// >>>> undefined
/// >>>> a has a value of undefined

```

When an undeclared variable is assigned a value, the JS engine \(in non-strict mode\) would automatically add the variable to the global object in the 1st phase of  code execution. 

```text
a1 = 3;
console.log('a1=', a1)

/// ------- output
/// for the above code  (assuming 'use strict' is not enabled),
/// the JS engine (in non-strict mode), would add 'a' to the global object
/// a1=3


/// in strict mode, for the above the JS engine will throw 
/// Uncaught Reference Error: a is not declared

```

![](../.gitbook/assets/1.mp4)

