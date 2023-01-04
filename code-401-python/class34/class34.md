# Read 34 : Context API

## What is Global State: [source](https://www.educative.io/answers/what-is-global-state-with-react)


**In React, originally, the state is held and modified within the same React component. In most applications, different components may need to access and update the same state. This is achieved by introducing the global states in your app. The main purpose of the global state is to share a state among multiple components.**

### There are three ways this communication can happen:

1. With a child component
2. With a parent component
3. With a sibling component


## Context API in React:[source](https://reactjs.org/docs/context.html)

### When to Use Context
Context is designed to share data that can be considered “global” for a tree of React components, such as the current authenticated user, theme, or preferred language. For example, in the code below we manually thread through a “theme” prop in order to style the Button component:



## Redux vs Context API: When to use them[source]()

### To use the Context API, you have to:

1. Create the Context

```
const Context = createContext(MockData);
```
2. Create a Provider for the Context

```
const Parent = () => {
    return (
        <Context.Provider value={initialValue}>
            <Children/>
        </Context.Provider>
    )
}
```

3. Consume the data in the Context
```
const Child = () => {
    const contextData = useContext(Context);
    // use the data
    // ...
}
```

### So What is Redux?

**It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test. On top of that, it provides a great developer experience, such as live code editing combined with a time-traveling debugger.**

**Redux is an Open Source Library which provides a central store, and actions to modify the store. It can be used with any project using JavaScript or TypeScript, but since we are comparing it to Context API, so we will stick to React-based Applications.**

### To use Redux you need to:

1. Create a Reducer
```
import { createSlice } from "@reduxjs/toolkit";

export const slice = createSlice({
    name: "slice-name",
    initialState: {
        // ...
    },
    reducers: {
        func01: (state) => {
            // ...
        },
    }
});

export const { func01 } = slice.actions;
export default slice.reducer;
```

2. Configure the Store
```
import { configureStore } from "@reduxjs/toolkit";
import reducer from "./reducer";

export default configureStore({
    reducer: {
        reducer: reducer
    }
});
```

3. Make the Store available for data consumption

```
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import App from './App.jsx'
import store from './store';

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById("root")
);
```

4. Use State or Dispatch Actions
```
import { useSelector, useDispatch } from 'react-redux';
import { func01 } from './redux/reducer';

const Component = () => {
    const reducerState = useSelector((state) => state.reducer);
    const dispatch = useDispatch();
    const doSomething = () = > dispatch(func01)  
    return (
        <>
            {/* ... */}
        </>
    );
}
export default Component;
```