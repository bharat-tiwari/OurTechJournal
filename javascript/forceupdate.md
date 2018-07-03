#forceUpdate() method

`forceUpdate()` method can be used to trigger a re-rendering whenever a value of some data/variable changes.

###### Note that re-render automatically triggers when a **local state** or a **props (connected to store)**  data/variable changes

`forceUpdate()` can be used if you want to trigger a re-rendering when some value/data like a class level variable changes its value, but its use should be avoided.

You should avoid use of `forceUpdate()`. If you find yourself using `forceUpdate()`, you’re probably doing something wrong. For values for which a change should trigger a re-render, you should use `local state` or props-Redux store.







