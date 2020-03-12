# Javascript Code Execution

## Javascript Statements

* code statements that just are there in the memory 
* can be used to do some computation / logic, but doesn't return anything e.g. if-statement or function body

## Javascript expressions

* code that returns some value from an assignment or other operator

  e.g. \* a=3; // returns 3

  * b === 'abc'; //returns true/false
  * anonymous function

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

