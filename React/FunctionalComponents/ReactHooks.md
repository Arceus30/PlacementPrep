# React Hooks

-   Don't Work inside classes

### 1. useState

-   `useState` allows components to manage state, declare state variables,objects,arrays and update them.
-   Setter is asynchronous in nature, the state is changed but its effect is realized after rerendering
-   **Note**: When updating state based on the previous state of an object, ensure to merge the new state with the existing state to prevent overwriting other properties. New variable should be created and returned and old variable should not be mutated

```jsx
import React, { useState } from "react";
function Example() {
    const [count, setCount] = useState(0); // Declaring a state variable named "count" with an initial value of 0
    const [person, setPerson] = useState({ name: "", age: 0 }); // object state
    const [list, setList] = useState([]); // array state

    const handleIncrement = () => {
        setCount(count + 1); // The setter function can be called with a new value,
        setCount((currentCount) => currentCount + 1); //or with a function that receives the previous state value and returns the new state value.
    };

    const handleUpdateName = () => {
        setPerson((prevPerson) => ({ ...prevPerson, name: "John" }));
    };
}
```

### 2. useEffect

-   allows to perform side effects. Side effects may include data fetching, subscriptions, or manually changing the DOM.
-   `useEffect(()=>{//sideEffect})`: executes after every rendered
-   `useEffect(()=>{//sideEffect}, [])`: executes once only when it is mounted or initially rendered
-   `useEffect(()=>{//sideEffect},[dependencies])`: executes when the dependencies changes
-   The function returned by useEffect is used for cleaning up after the side effect: it acts as the cleanup function and executes when the component is unmounted, it removes any subscription or event handler
-   the useEffect callback cannot be asynchronous, but you can define an asynchronous function inside and call it immediately.

### 3. useContext

-   allows to subscribe to React context without introducing nesting. Context provides a way to pass data through the component tree without having to pass props down manually at every level.

```jsx
// app.jsx
export const myContext = React.createContext(defaultVal); // it Creates the Context
// initial value can be set inside the defaultVal or in the value props written along with Provider

function app(){

// Wrap the components that need access to the context with a 'Provider'
return (
    <myContext.Provider value={}>
    {
        // any Component can now use 'useContext' hook to access the values
        <MyComponent/>
    }
    </myContext.Provider>
    )
}

// 1st way to use context
//MyComponent.jsx
import {myContext} from 'app'
function MyComponent(){
    return (
        <myContext.Consumer>
        user => {
            return <div> {user} </div>
        }
        </myContext.Consumer>
    )
}

// 2nd way to use context
import {useContext} from 'react'
import {myContext} from 'app'
function MyComponent(){
    const user = useContext(myContext);
    return <div> {user} </div>;
}
```

### 4. useReducer

-   Hook for state management
-   useState is built using useReducer
-   Returns a pair of [newState, dispatch]
-   Action and initialState can be object
-   We can share the state using the useContext hook

```jsx
const initialState;
const reducer = (state, action)=>{}
const [count, dispatch] = useReducer(reducer, initialState);

return (
    <div>
        <button onClick={()=>{dispatch('increment')}}> Increment </button>
        <button onClick={()=>{dispatch('decrement')}}> Decrement </button>
    </div>
);
// These dispatch inputs are passed to the action parameter of the reducer
```

**Difference in useState and useReducer**
|Case|useState|useReducer|
|-|-|-|
|Type of state|Number, String, Boolean|Object or Array|
|Number of state tranisitions|1-2|Too many|
|Related State transitions|No|Yes|
|Business Logic|No|Complex|
|State|Local|Global|

### 5. useCallback

-   used for optimizing performance by memoizing callback functions that only changes if one of the dependencies has changed

```jsx
// file which has created a memoizedCallback
import { useCallback } from "react";
const memoizedCallback = useCallback(func, dependencies);

// this memoizedCallback function is passed to the children as props
```

-   Various ways to pass dependencies
    -   `const memoCallback = useCallback(func)`: it will be memoized only once and the func remains constant for lifetime
    -   `const memoCallback = useCallback(func,[])`: it will be memoized only once and the func remains constant for lifetime, the callback does not depend on any external variables.
    -   `const memoCallback = useCallback(func,[dependencies])`: it will be memoized only when dependency changes

### 6. useMemo

-   React Hook that allows you to memoize the result of a function call and recompute it only when its dependencies change.
-   `const memoVal = useMemo(func, dependencies)`
-   Various ways to pass dependencies
    -   `const memoCallback = useMemo(func)`: Value is computed only once remains same for lifetime
    -   `const memoCallback = useMemo(func,[])`: Value will be computed only once and the callback does not depends on any external variables.
    -   `const memoCallback = useMemo(func,[dependencies])`: Value will be computed only when dependency changes

### 7. useRef

-   React Hook that provides a way to create mutable references that persist across renders without causing re-renders when the reference changes
-   it should not be used in dom manipulation as it does not rerenders, usually used to store previous values like props

```jsx
const myRef = useRef();
myref.current; // access referenced value
<input ref={myRef} />; // ref can be attached to a DOM element by passing it to the ref attribute
```

### 8. CustomHooks

-   Custom hooks in React are JavaScript functions that utilize React's useState, useEffect, useContext, and other hooks to encapsulate reusable logic. They are typically created to share logic that can be used across multiple components, improving code organization and reusability.

```jsx
import { useState, useEffect } from "react";
function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    useEffect(() => {
        async function fetchData() {
            try {
                const response = await fetch(url);
                const result = await response.json();
                setData(result);
                setLoading(false);
            } catch (error) {
                console.error("Error fetching data:", error);
                setLoading(false);
            }
        }
        fetchData();
    }, [url]);
    return { data, loading };
}

// Usage in a component
function MyComponent() {
    const { data, loading } = useFetch("https://api.example.com/data");

    if (loading) {
        return <p>Loading...</p>;
    }

    return (
        <div>
            {data && (
                <ul>
                    {data.map((item) => (
                        <li key={item.id}>{item.name}</li>
                    ))}
                </ul>
            )}
        </div>
    );
}
```
