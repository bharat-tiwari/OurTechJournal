#Storing Data in React


- Data local to a component i.e. data which is not required to be shared across app or components:


      
      1. Use component's local **state** 

           - Use `this.state.onChange()` method to change the local state data and trigger a re-render of DOM
     
     
     2. Use class level variable
  
     e.g. `public someLocalVar `
     or `private someLocalPrivateVar`
     
     Do not use class level variable for anything that you want to trigger re-rendeing of DOM
     

- Data to be used across application or across multiple components:

      1. Use Redux store and associate/connect your props variables with the global Redux store using the **connect** wrapper and a **mapStateToProps** function.
