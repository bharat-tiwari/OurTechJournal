#Event Bubbling
When some event occurs on an HTML element, it would first execute the eventHandlers associated with that element and event. Then the event would be bubbled up to the element's parent. Any eventHandler defined/ associated with the parent element for that event would get executed. And so on until the event reaches the root `document` element. some events even reach window, calling all handlers on the path.

# `event.target`
points to origin/original target element that triggered the event. 
Note that all eventHandler functions get `event` as first parameter to the function. Thus the eventHandler function of any parent element in the event-bubble path can figure out who was the original target element using `event.target`

# `event.currentTarget` 
points to current target element in the event-bubble path whose eventHandler is  currently running.

# How to stop event from bubbling up
User `event.stopPropogation`

It would stop the current event from bubbling up to the parents

If there are multiple eventHandlers for a given event on an element, `event.stopPropogation` called from any of the eventHandlers would stop the event bubbling up to the parents.

 However, for the current target, all other event handlers would continue to run. 
 If you want to stop the other running event handlers as well for the current target, call the method `event.stopImmediatePropogation`

 

