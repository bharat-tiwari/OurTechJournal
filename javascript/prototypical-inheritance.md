# Prototypal Inheritance

*** Most of the things we have learnt about Javascript prototypal inheritance is from the wonderful [video series by Anthony Alecia](https://youtu.be/g52qWGmSxjw?list=PLIn1Yut6MvccYKkaDHDJKECpN1LMDTpha.).

 
 

Inheritance
= a language feature that allows an object to access the properties and methods of another object.

## Class-based or Classical Inheritance
In class-based inheritance, given a `ClassA`, you can inherit `ClassB` from `ClassA` so that `ClassB` can access all the public/protected properties and methods of `ClassA`. To inherit, the language would provide keyword like `inherits` or operator like `:` .

## Prototypal Inheritance
In Javascript, whenever we create an object, les say `Obj1`, an internal property called `proto` gets created. This `proto` property points to an empty object to start with. To this `proto` object, we can add any property , lets say `prop2`. We can access this property as `Obj1.prop2`. Javascript engine would look for `prop2` in `Obj1`, when it won't find the property as direct child of `Obj1`, it would start looking for it under Obj1's proto object. Thus a property under `proto` object can be accessed directly using dot notation on `Obj1`.

The `proto` object can itself have another `proto` property that you may use to add more properties and methods, lets say another property `prop3` is added to the `Obj1.proto.proto`. And this property can again be accessed with dot operator on 'Obj1' like `Obj1.prop3`. Thus it may have a **prototypal chain**.

However at the bottom of the chain, there would always be an empty 'proto' object. This is called the base 

![](/assets/proto.png)

  

### Everything in javascript, that is not a primitive type, is an object. Arrays, functions are all javascript objects having a prototype.