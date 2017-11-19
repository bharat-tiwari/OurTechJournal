#Observables



Consider Netflix service, it gets continuously populated with new movies over time. We , the  subscribers of Netflix, get notified about the new additions to their movies collection (via website or email subscription or notifications) and then its upto us how and when we watch this new movies. 

Observables is similar concept.
Data coming from source can be regarded as a stream of data that would get populated asynchronously over time. When this data is processed using some methods of an Observable API (like RxJS), then the Observable API converts that data to a 'subscribe-able' stream of data that gets populated asynchronously over time. Your app can subscribe to the data provided via Observable API so that the app gets notified whenever there is new data available in the Observable data stream.


Observables is not limited to 'asynchronous' data, it can also wrap 'synchronous' data as well to make it 'subscribe-able'  or 'observable'.

Our app function that 'subscribes' to some observable data is called 'observer' - its observing or watching the changes happening to data, gets notified about data changes and now its upto our app function how to handle and use that new data or when its notified about some **error** or its notified that the data changes are **complete** or **done**. 

An `observer` or `subscriber` would provide one or more of the below methods to observable :

* next()
* error()
* complete()


```js

const button = document.querySelector('testButton');

const anObserver = {
    next: (val)=>console.log(val),
    error: (err)=>console.log(err),
    complete:()=>console.log('Stream complete')
}

Rx.Observable.fromEvent(button, 'click') //👈 Rx.Observable provides lot of such methods like fromEvent to create an Observable from an event or data fetch or any async action
    .subscribe(anObserver);
    
```


