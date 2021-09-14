# React Testing Library

```text
 @testing-library/react, jest
```

{ `render` } from the react-testing-lib allow us to mount/render a component in virtual memory 

{ `screen` } from the lib allow us to read the rendered HTML

`screen` has few methods to query elements from the rendered HTML, can be used to confirm the expected elements are rendered - 

```text
const myElement = screen.getByText("some Text");
expect(myElement).toBeInTheDocument()
```

 `getByText`, `getByTestId` \(uses `data-testid` attribute\), `getByAltText` etc. methods can be used

To Test a component linked to redux, render it wrapping inside `<Provider>`  with its's store attribute set to mock store data

```text
import { render } from '@testing-library/react';
import { Provider } from 'react-redux';
import { createStore } from 'redux';

// .... inside some test
const store = createStore(appReducer, initialState);
const { rerender, ...rest } = render(
    <Provider store={store}>
      <Component {...props} />
    </Provider>,
  );
  
// use rerender, to rerender with some new store values

```











