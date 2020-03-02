# typeof vs instanceof

Quickest/Easiest explanation

[https://stackoverflow.com/a/6625960](https://stackoverflow.com/a/6625960)

## Use `instanceof` for custom types:

```text
var ClassFirst = function () {};
var ClassSecond = function () {};
var instance = new ClassFirst();
typeof instance; // object
typeof instance == 'ClassFirst'; //false
instance instanceof Object; //true
instance instanceof ClassFirst; //true
instance instanceof ClassSecond; //false
```

## Use `typeof` for simple built in types:

```text
'example string' instanceof String; // false
typeof 'example string' == 'string'; //true

'example string' instanceof Object; //false
typeof 'example string' == 'object'; //false

true instanceof Boolean; // false
typeof true == 'boolean'; //true

99.99 instanceof Number; // false
typeof 99.99 == 'number'; //true

function() {} instanceof Function; //true
typeof function() {} == 'function'; //true
```

## Use `instanceof` for complex built in types:

```text
/regularexpression/ instanceof RegExp; // true
typeof /regularexpression/; //object

[] instanceof Array; // true
typeof []; //object

{} instanceof Object; // true
typeof {}; //object
```

And the last one is a little bit tricky:

```text
typeof null; //object
```

