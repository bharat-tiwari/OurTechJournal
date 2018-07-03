#Redux

With Redux, we get a global **store**. This store lives at the highest level of your app and passes data down to all children. 
You connect to the global store with the **connect** wrapper and a **mapStateToProps** function.

You use `this.props.dispatch(actionName)` to trigger an action function that you have defined in you redux setup to update something globally

* When props are updated via dispatching an action in Redux store, it also triggers a re-render - just like when we update some local **state** data/variable



