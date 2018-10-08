#Error Handling in React

### Error boundaries (in React 16+)
Use `componentDidCatch` in the Error Boundary component and wrap your error prone child components or the whole App inside this Error Boundary component.

Error boundaries cannot catch errors that could happen in some async call or in some event handler 


### Use try-catch and window.onerror
handle errors in catch blocks, throw meaningful errors and propogate errors up till window


### have a Global Logger provider to Log errors to your cloud watch or somewhere in server
call this global logger in `window.onerror`

### Use Sentry or Catch.js to log the errors that happen on client side to the server
 