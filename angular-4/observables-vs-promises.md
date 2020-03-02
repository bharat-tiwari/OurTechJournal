# Observables vs Promises

[https://stackoverflow.com/a/37365955](https://stackoverflow.com/a/37365955)

**Promise** can handle only a single time when an async operation is completed \(either success or error\)

Note: There are Promise libraries out there that support cancellation, but ES6 Promise doesn't so far.

 **Observable**

An Observable , like explained in previous topic, can handle a stream of events happening over time to call the callback\(_next_, _error_, _complete_ functions\) each time the event happens in the series.

_Observable_ provides some bonus features over _Promise_. With Observable you can handle an event zero, single or multiple times. You can utilize the same API in each case.

Observable also has the advantage over Promise to be cancelable. If the result of an HTTP request to a server or some other expensive async operation isn't needed anymore, the Subscription of an Observable allows to cancel the subscription, while a Promise will eventually call the success or failed callback even when you don't need the notification or the result it provides anymore.

Observable provides operators like map, forEach, reduce, ... similar to an array, to customize the incoming data.

It also provides some very useful operators like retry\(\), or replay\(\), ... that are often quite handy.

