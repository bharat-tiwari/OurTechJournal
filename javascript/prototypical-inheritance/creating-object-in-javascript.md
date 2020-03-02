# Creating Object in Javascript

1. Using Object literal

   ```javascript
    var obj = new Object();
   ```

2. Using Function Constructor

   ```javascript
    var tom = new Avatar();
   ```

3. Using `Object.create`

   ```javascript
    var obj1 = Object.create(o)
   ```

   `Object.create` creates a new object with its prototype object passed as a parameter \(obj2 in above example\).

4. Using curly brackets syntax

   ```javascript
    var obj1 = {}; // This is equivalent to Object.create(null) method, it would set the created object's prototype =null .
   ```

5. In ES6, we use class pattern

