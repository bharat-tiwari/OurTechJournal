# Maps

A `Map` is a new object type in ES6 that represents a data structure to hold a collection of `key-value` pairs. A key in Map can be of any type - any primitive type, symbol, date, object or a function can be a key. Same holds for the values.

## Create Map

```javascript
// create map
let coolDude = new Map();

// set key-value pairs for the map
coolDude.set('wears', ['Red Shirt', 'Green Pant', 'Sunglasses (even in night)']);
coolDude.set('drives', 'Red Mustang');

// you can chain the set
coolDude.set('drinks', '7-up')
        .set('speak', (words: string) => `Yo!Wazzup!${words}`;
```

### Initialize Map with an array:

The following JSFiddle creates a Map of few commonly needed regular expression , like for phone number or email address, initialized with an array. The react component uses this map to validate values entered in email or phone fields.

[JSFiddle Example](https://jsfiddle.net/tiwarib/uh9yL1um/#tabs=result,js,html,css)

