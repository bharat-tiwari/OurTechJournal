# Promise Error: Catch vs Error Function in Then

[https://stackoverflow.com/a/33278420](https://stackoverflow.com/a/33278420)

```javascript
somePromise.then(() => {
   // if some error happens here, it will be caught in 'catch'
   anErrorThrowingFunction('some wrong param');
}).catch((err) => console.log('Errror occured'));

// below will yield similar result as above, the errorHandler tries to catch any unhandled error
// from previous result.
somePromise.then(() => {
   // if some error happens here, it will be caught in 'catch'
   anErrorThrowingFunction('some wrong param');
}).then(null, errorHandler);



/// in below example, the error in Success function of then won't be caught
somePromise.then(() => {
   // if some error happens here, it will be caught in 'catch'
   anErrorThrowingFunction('some wrong param');
}, (err) => console.log('error'));
```

