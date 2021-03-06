# Prototypal Inheritance

_\*_ Most of the things we have learnt about Javascript prototypal inheritance is from the wonderful [video series by Anthony Alecia](https://youtu.be/g52qWGmSxjw?list=PLIn1Yut6MvccYKkaDHDJKECpN1LMDTpha.).

Inheritance = a language feature that allows an object to access the properties and methods of another object.

## Class-based or Classical Inheritance

In class-based inheritance, given a `ClassA`, you can inherit `ClassB` from `ClassA` so that `ClassB` can access all the public/protected properties and methods of `ClassA`. To inherit, the language would provide keyword like `inherits` or operator like `:` .

## Prototypal Inheritance

In Javascript, whenever we create an object, lets say `Obj1`, an internal property called `proto` gets auto-created for the object. This `proto` property points to a base object. To this `proto` object, we can add any property , let's say `prop2`. We can access this property as `Obj1.prop2`. Javascript engine would look for `prop2` in `Obj1`, when it won't find the property as direct child of `Obj1`, it would start looking for it under obj1's `proto` object. Thus a property under `proto` object can be accessed directly using dot notation on `Obj1`.

\(in Chrome V8, this `proto` property of any object is referred as **proto**: \`myObject.**proto**.**proto**.....\)

The `proto` object can itself have another `proto` property that you may use to add more properties and methods, let's say another property `prop3` is added to the `Obj1.proto.proto`. And this property can again be accessed with dot operator on 'Obj1' like `Obj1.prop3`. Thus it may have a **prototypal chain**.

## Base prototype object

At the bottom of the prototypal chain, there would always be a base object. This is called the base object. Base object is called 'Object', its at the very bottom of the prototypal chain and have some predefined methods and properties like `ToString`, `hasOwnProperty`, `isPropertyOf`, `valueOf` etc.

![](../../.gitbook/assets/proto.png)

### Everything in javascript, that is not a primitive type, is an object. Arrays, functions are all javascript objects having a prototype.

## Function objects

Functions in javascript are objects. The prototype object for a function is `Empty` function:

```javascript
function Empty(){}
```

This Empty function, which is prototype for all the functions in javascript has some predefined properties and methods like:

```javascript
arguments: an array of the arguments of the function.
call, bind, apply - functions that allow you to pass an object to which `this` would point to in the function and then list of parameters.
name: name of the function
```

This `Empty` function which is prototype for the function would have its prototype set to the **base object: `Object {}`**.

## Array objects:

Arrays in javascript are objects. The prototype object for arrays is `[]`, an empty array.

this empty array prototype for array objects has properties like `length`, `indexOf`, `forEach`, `filter`, `map`, `keys`, `join`, `pop`, `push`, `reduce`, `reverse` etc.

This `[]` array which is prototype for any array would have its prototype set to the **base object: `Object {}`**.

