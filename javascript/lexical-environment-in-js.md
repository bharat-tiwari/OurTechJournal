# Lexical Environment in JS

**Lexical Environment** of a variable = where it sits physically in the code \( i.e. inside a function or within global context, or within some if statement or for loop etc. or a code scope created by wrapping the code inside a pari of curly brackets {..} \)

**Lexical Environment** is created every time you create a scope using the curly brackets {}. It can be nested: {{…}}

[check this out](https://medium.com/@js_tut/javascript-tutorial-lexical-environment-3ee161bb2295)

## `var` vs `let/const`

The **let** and **const** keywords conceal the variable to its own lexical environment/scope. It provides data privacy because sometimes you want to _limit the use of a variable to a scope_.

The **var** keyword “hoists” \(or lifts up\) the variable definition \(its name\) up all the way to the _**global scope**_. Regardless what _**block-scope**_ your variable is defined in using **var**, it always becomes available at the uppermost scope.

For these reasons the **let/const** keywords are considered to be a “safer” alternative to the **var** keyword, even though in a few cases they produce exactly the same behavior. The difference is that **let/const** always conceals to the scope its defined in.

There are exceptions. Variables defined inside _**function-scope**_ are concealed to it — regardless of whether you used **var** or **let**. This is also true of _**callback**_ functions \(which are essentially are _**function-scope**_.\)





