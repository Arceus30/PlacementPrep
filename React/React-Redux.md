## React Redux

-   stores the state of application (state of an application is the state represented by all the individual components of the app)
-   action describes the changes in the state
-   reducer which carries out the transition depending on action

```bash
npm i redux
npm i react-redux
npm i @reduxjs/toolkit
```

```jsx
// counterSlice.jsx
import { createSlice } from "@reduxjs/toolkit";
export const counterSlice = createSlice({
    name: "counter",
    initialState: {
        value: 0,
    },
    reducers: {
        // no return statement is required from these functions.
        increment: (state) => {
            state.value += 1;
        },
        decrement: (state) => {
            state.value -= 1;
        },
        incrementByAmount: (state, action) => {
            state.value += action.payload;
        },
    },
});
// Action creators are generated for each case reducer function
export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;

// store.js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./counterSlice";

export default configureStore({
    reducer: {
        counter: counterReducer,
    },
});

// main.jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import store from "./store";
import { Provider } from "react-redux";

ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
        <Provider store={store}>
            <App />
        </Provider>
    </React.StrictMode>
);

//Counter.jsx
import React from "react";
import { useSelector, useDispatch, connect } from "react-redux";
import { decrement, increment } from "./counterSlice";

export function Counter() {
    const count = useSelector((state) => state.counter.value);
    const dispatch = useDispatch();

    return (
        <div>
            <div>
                <button onClick={() => dispatch(increment())}>
                    Increment
                </button>
                <span>{count}</span>
                <button onClick={() => dispatch(decrement())}>
                    Decrement
                </button>
            </div>
        </div>
    );
}

// connect(): read values from the Redux store (and re-read the values when the store updates)
const mapStateToProps = (state)=>{
    // called every time the store state changes. It receives the entire store state, and should return an object of data this component needs, an object of values in the state
}

// mapDispatchToProps
// this parameter can either be a function, or an object.
//1.) if it’s a function, it will be called once on component creation. It will receive dispatch as an argument, and should return an object full of functions that use dispatch to dispatch actions.
const mapDispatchToProps = (dispatch)=>{
    }
// 2.) If it’s an object full of action creators, each action creator will be turned into a prop function that automatically dispatches its action when called
const mapDispatchToProps = {}



// `connect` returns a new function that accepts the component to wrap:
// 1.)
const connectToStore = connect(mapStateToProps, mapDispatchToProps)
// and that function returns the connected, wrapper component:
const ConnectedComponent = connectToStore(Component)
// OR
// 2.) We normally do both in one step, like this:
connect(mapStateToProps, mapDispatchToProps)(Component)
```

### 1. Redux-Persist
