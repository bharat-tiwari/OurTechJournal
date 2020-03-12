# var vs let/const

## `var` vs `let/const`

The **let** and **const** keywords conceal the variable to its own lexical environment/scope. It provides data privacy because sometimes you want to _limit the use of a variable to a scope_.

The **var** keyword “hoists” \(or lifts up\) the variable definition \(its name\) up all the way to the _**global scope**_. Regardless what _**block-scope**_ your variable is defined in using **var**, it always becomes available at the uppermost scope.

For these reasons the **let** keyword is considered to be a “safer” alternative to the **var** keyword, even though in a few cases they produce exactly the same behavior. The difference is that **let** always conceals to the scope its defined in.

There are exceptions. Variables defined inside _**function-scope**_ are concealed to it — regardless of whether you used **var** or **let**. This is also true of _**callback**_ functions \(which are essentially are _**function-scope**_.\)

