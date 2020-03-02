# Event Delegation

Because of the fact that events get bubbled up from the target element to its parents, we can use event bubbling to handle the events on multiple children elements by defining a single event handler on the parent of all these children.

Also, using the `event.target` property, we can find out exactly which of the children was the original target and using some data-attributes on the HTML of the children we can selectively apply \(e.g. using if or switch conditions on the data-attributes \) certain specific actions for specific targets.

Thus we can delegate the eventHandlers for some specific child element or specific groups of children \(e.g. all children `div` elements that have `data-selected` attribute = true\) to a single eventHandler on the parent element, saving ourselves from writing individual eventHandlers on each of the children.

