#React Ref System

When working with React, you usally are working with virtual DOM elements that react would finally render to actual DOM as needed. However, there are some cases where you might have to interact with the actual elements. For such cases, React provides a ref system.


## Creating a Ref

just pass a callback that assigns to a property:

```
class MyComponent extends Component {

   /**
    *@name render
   **/
   render() {
     return (
       <div>
         <input ref={ input => this.myInput = input }
       </div>
     );
   }
   
   /**
    *@name alertInput
   **/
   alertInput() {
       const value = this.myInput.value;
       alert(value);
   }

}
```




