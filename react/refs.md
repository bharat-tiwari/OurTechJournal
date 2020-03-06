# refs

When working with React, you usally are working with virtual DOM elements that react would finally render to actual DOM as needed. However, there are some cases where you might have to interact with the actual elements. For such cases, React provides a ref system.

## Creating a Ref using `createRef` method \( in React 16.3+\)

1. Create an class-level `ref` variable using  `React.createRef()` 
2. Assign the `ref` attribute of the element that you want to access  to in DOM to the above created ref variable.
3. After the component has been rendered/mounted, the element's DOM reference can be accessed using the `current` property of the ref variable. 

```text
import React, { createRef } from "react";

class RefExample extends React.Component {

  myDivRef = createRef();
  
  componentDidMount() {
      const myDiv = this.myDivRef.current;
      myDiv.scrollIntoView({ block: 'center' });
      
  }

  

  render () {
    return (
      <div ref={this.myDivRef}>
        <ChildComponent>{this.props.children}</ChildComponent>
      </div>
    );
  }
}

export default MyComponent;
```



## Creating a Ref using callback Refs \( in older React versions\)

just pass a callback that assigns to a property:

```text
class MyComponent extends Component {
   myInput = null;
   
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

