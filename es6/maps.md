# ES6 Maps


A `Map` is a new object type in ES6 that represents a data structure to hold a collection of `key-value` pairs.
A key in Map can be of any type - any primitive type, symbol, date, object or a function can be a key. Same  holds for the values.

## Create Map 

```js
// create map
let coolDude = new Map();

// set key-value pairs for the map
coolDude.set('wears', ['Red Shirt', 'Green Pant', 'Sunglasses (even in night)']);
coolDude.set('drives', 'Red Mustang');

// you can chain the set
coolDude.set('drinks', '7-up')
        .set('speak', (words: string) => `hey!wazzup!${words}`; 
        
```

### Initialize Map with an array:

```js
let regExes = new Map([
  'phoneNumber': new RegEx(),
  'SSN': new RegEx(),
  'paymentAmount' : () => 

]);
```




