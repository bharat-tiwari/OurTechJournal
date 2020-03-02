# Event handlers

## Event Handlers

3 ways to add event handler to an HTML element:

1. using the HTML attribute e.g. `onclick` or `onmouseover`

   ```markup
    <button onclick="makePayment()" id="paymentSubmit">Make Payment</button>
   ```

2. Using DOM in JS

   ```javascript
    let paymentButton = document.querySelector('#paymentSubmit');
    paymentButton.onclick = makePayment;
   ```

   \*note: here we don't use parenthesis with the method name\( not `makePayment()` , just `makePayment`\)

   To remove the handler,

   ```javascript
        paymentButton.onclick = null;
   ```

3. Using `addEventListner` method - allows to add multiple eventListeners by calling the method multiple times on the element

   ```javascript
    let paymentButton = document.querySelector('#paymentSubmit');
    paymentButton.addEventListner('click', makePayment);
   ```

   With this, we can remove the event listener using `removeEventListner` method:

## Event Object

On occurrence of an event, the browser would create an `Event` object and pass it as first argument to the event handler function. This `Event` object carries details of the event, it would have properties depending on the type of the event, below are some common properties

* `type` : type of the event - `click` or `keyup` or `mouseout` etc
* `target`: [See in event bubbling](event-handlers.md) 
* `currentTarget`: [See in event bubbling](event-handlers.md) 
* `clientX/clientY`: pixel coordinates of the mouse position that triggered the event if its a mouse event.

