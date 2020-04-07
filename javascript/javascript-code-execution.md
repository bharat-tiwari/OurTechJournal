# Javascript Code Execution

## Javascript Statements

* code statements that just are there in the memory 
* can be used to do some computation / logic, but doesn't return anything e.g. if-statement or function body

## Javascript expressions

* code that returns some value from an assignment or other operator

  e.g. \* a=3; // returns 3

  * b === 'abc'; //returns true/false
  * anonymous function
  * 

## JS Execution is single threaded

Single threaded = one command at a time 

Some languages are multi-threaded, that means the language might be running multiple pieces of code in multiple threads in  parallel at a time.

But javascript is single threaded

\(the Browser program , under the hood, may give multi-threaded behavior to the JS code, but for our/developer's perspective JS is running in single thread\)

## JS Execution is synchronous

Synchronous execution = one line of code at a time and in the order\(top to bottom\)

Javascript execution is synchronous always 

\(Asynchronous JS code execution for example like in AJAX feels like or behaves like Asynchronous but there too javascript execution is synchronous\)



## Code Execution flow

* Top to bottom
* Two cycles
  * 1st cycle \( also called **Hositing**\)
    * starts from the top of the code to bottom
    * goes through all the code and puts all variables/object/function definitions in memory as properties of 'global' object
    * skips any execution or evaluation code, e.g. a function call or boolean evaluation or assignment is skipped
  * 2nd cycle:
    * starts from the top of the code to bottom
    * starts execution and evaluation of any function calls, or assignments or evaluations.

![](../.gitbook/assets/jscodeexecution.png)

