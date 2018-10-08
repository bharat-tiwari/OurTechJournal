#React Context

React Context (_in React 16+ versions_) allows you to pass some data down the component tree without having to pass it via `props` from parent to child to further down the component tree.

1. Create the context in a component from where you want data to be passed on down the component tree using `React.createContext` which returns an object with `Provider` and `Consumer` components

2. to the `Provider` component a prop named `value` needs to be provided that can have any value, it could be a string or a number or can be some complex object

3. In the children component, this value can be accessed a parameter to a function wrapped inside the `Consumer` component.