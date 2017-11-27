#Creating Object in Javascript

1. Using Object literal

    ```js
    var obj = new Object();
    ```

2. Using Function Constructor
    ```js
    var tom = new Avatar();
    ```

3. Using `Object.create`
    ```js
    var obj1 = Object.create(o

    `Object.create` creates a new object with its prototype object passed as a parameter (obj2 in above example).

4. Using curly brackets syntax

    ```js
    var obj1 = {}; // This is equivalent to Object.create(null) method, it would set the created object's prototype =null .
    ```
    
5. In ES6, we use class pattern
    