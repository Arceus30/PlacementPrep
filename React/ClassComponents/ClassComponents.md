# Class Components:

-   Statefull Component

### 1. LifeCycle Methods

-   **Mounting**: When an instance of a component is being created and inserted into DOM
    -   `constructor(props)`:
        -   if custom constructor is defined then `super(props)` must be called first
        -   special function that will be called automatically everytime a new component is created
        -   initializes states and binding the event handlers
        -   do not cause side effects
    -   `static getDerivedStateFromProps(props,state)`:
        -   state of the component depends on changes in props over time
        -   set the state
        -   do not cause side effects
    -   `render()`:
        -   only required method
        -   read props and state and return JSX
        -   Do not change state, interact with DOM, make ajax calls
        -   children components lifecycle methods are also executed
    -   `componentDidMount()`:
        -   invoked immediately after a component and all its children are rendered
        -   Cause side effects, interact with DOM, make ajax calls
-   **Updating**: When a component is being rerendered as a result of changes to either its props or state
    -   `static getDerivedStateFromProps(props,state)`:
        -   state of the component depends on changes in props over time
        -   set the state
        -   do not cause side effects
    -   `shouldComponentUpdate(nextProps,nextState)`:
        -   dictates if component should re-render or not
        -   do not cause side effects
    -   `render()`:
        -   only required method
        -   read props and state and return JSX
        -   Do not change state, interact with DOM, make ajax calls
        -   children components lifecycle methods are also executed
    -   `getSnapshotBeforeUpdate(prevProps,prevState)`:
        -   called right before the changes from virtual DOM are to be made in DOM
        -   Returned value is passed as the third parameter to the next method
    -   `componentDidUpdate(prevProps, prevState, snapshot)`:
        -   called after the render is finished in the rerender cycle
        -   cause side effects
        -   can make ajax calls after comparing previous props and state with new props and state
-   **Unmounting**: When a component is being removed from the DOM
    -   `componentWillUnmount()`:
        -   immediately invoked before a component is unmounted or destroyed
        -   cancels any network requests, removes event handlers, cancel any subscriptions, invalidate timers
        -   do not call the setState method
-   **Error Handling / Error Boundaries**: When there is an error ocurred during rendering, in a lifecycle method, or in the constructor of any child component, By default complete details of error are shown in development mode but not in production mode, this error handler does not catch errors inside any event handler
    -   `static getDerivedStateFromError(error)`: update state in response to an error condition.
    -   `componentDidCatch(error, info)`: it is used to log the errors and information about the error
    -   Component which may throw error is passed as props.children to this class
    -   ```jsx
        class ErrorBoundary extends React.Component {
            constructor() {
                super();
                this.state = {
                    hasError: false,
                };
            }
            static getDerivedStateFromError(error) {
                return {
                    hasError: true,
                };
            }
            render() {
                if (this.state.hasError) {
                    return <h1>Something is not right</h1>;
                } else {
                    return this.props.children;
                }
            }
        }
        ```

### 2. Pure Component

implements shouldComponentUpdate with a shallow props and state comparison, whereas regular components returns true by default

```jsx
import React from "react";
class PureComp extends React.PureComponent {}
```

### 3. Props:

-   passing data from parent to child components as attributes, these are immutable `<welcome name={}/>`
-   Inside a class component, props are accessed like this `this.props.name`
-   when methods are passed as props only function definition is passed and not the function call
-   Default Props: this should be done before exporting and after defining the functional component
-   PropTypes: use to specify the type of the props received
-   JSX can be passed as children prop and can be accessed by `props.children`
-   ```jsx
    import React from "react";
    import PropTypes from "prop-types";
    class Welcome extends React.Component {
        // Default Props
        static defaultProps = {
            name: value,
        };

        // PropTypes
        static propTypes = {
            name: PropTypes.string,
        };

        render() {
            return <h1>Hello {this.props.name}</h1>;
        }
    }

    //app.jsx
    //1st way
    <Welcome/>

    //2nd way
    <Welcome>
        {
            // Children prop
            <p></p>
        }
    </Welcome>;
    ```

### 4. State

-   ```jsx
    import React from "react";
    class Example extends React.Component {
        constructor(props) {
            super(props);
            this.state = {
                count: 0,
            }; // Declaring a state variable named "count" with an initial value of 0
        }
        handleIncrement() {
            this.setState(
                (prevState) => ({
                    count: prevState.count + 1,
                }), // it uses previous state to update current state
                () => {
                    console.log(this.state.count); // updated value of state variables can be accessed inside the callback function
                    // This function executes 'first' after the page rerenders
                }
            );
        }
        render() {
            return (
                <div>
                    <p>You clicked {this.state.count} times</p>
                    <button onClick={() => this.handleIncrement()}>
                        Click me
                    </button>
                </div>
            );
        }
    }
    ```

### 5. Event Handling and Binding

-   `onClick`, `onSubmit`,`onChange`, etc and we can define functions which triggers depending on the events, these functions are called event handlers
-   only Function definition is passed as event handler and not the function call
-   when method inside the class components are binded they are binded to the binding class only and not to the child component accepting those methods as props, this keyword refers to the parent Component and not the child component
-   ```jsx
    class Component extends React.Component {
        constructor() {
            super();

            // 3rd way of event binding
            this.handleChange = this.handleChange.bind(this);
        }
        handleChange() {} // Event Handler

        // 4th way of event binding
        handleChange() => {}

        render() {
            return (
                <input type="text" onChange={this.handleChange} />; // event handler handleChange is trigerred if the input value is changed
                // here this value is undefined since this keyword is not binded to that event handler

                // Event Bind
                // 1.) .bind()
                <button onClick={this.handleIncrement.bind(this)}>Click me</button>;

                // 2.) using an arrow function to wrap the event handler
                <input
                    type="text"
                    onChange={() => {
                        this.handleChange();
                    }}
                />
            );
        }
    }
    ```

### 6. Form Handling

-   ```jsx
    constructor(){
        super();
        this.state = {
            username: '',
        }
    }
    handleChange = ()=>{
        this.setState((event)=>{
            username: event.target.value, // event refers to form event, event.target refers to the element which triggered the event handler, event.target.value refers to the value of that element
        })
    }

    <form>
        <input type='text' value = {this.state.username} onChange = {this.handleChange}/>
    </form>;

    // Another way:
    constructor(){
        super();
        this.state={
            form:{},
        }
    }
    handleChange = (e) => {
        this.setState((prevState)=>{ ...prevState.form, [e.target.name]: e.target.value });
    };
    ```

### 7. Ref

-   create a ref object which can be attached to React elements or components. Refs provide a way to access DOM nodes or React elements created in the render method. Parent component can create ref object to child components
-   ```jsx
    import React from "react";
    class MyComponent extends React.Component {
        constructor() {
            super();
            this.hRef = React.createRef();
        }
        render() {
            return <h1 ref={this.hRef}>Hello, {props.name}!</h1>;
        }
    }

    // Ref forwarding: React.forwardRefs()
    class parentComponent extends React.Component {
        constructor(props) {
            super(props);
            this.ref = React.createRef();
        }
        clickHandler = () => {
            this.ref.current.focus();
        };
        render() {
            return (
                <div>
                    <Component ref={this.inputRef} />
                    <button onClick={this.clickHandler}></button>
                </div>
            );
        }
    }

    const Component = React.forwardRef((props, ref) => {
        return (
            <div>
                <input type="text" ref={ref} />
            </div>
        );
    });
    ```

### 8. Portals

-   provide a way to render children components into a different DOM subtree than the parent component's subtree.
-   useful when content is rendered into a DOM node that is outside the parent component's hierarchical tree, such as a modal, a tooltip, or a dropdown menu that needs to break out of its container for styling or positioning reasons.
-   ```jsx
    const MyComponent = (props) => {
        return ReactDOM.createPortal(JSX, document.getElementById(id));
    };
    ```

### 9. Higher Order Components(HOC)

-   A function takes a component as an argument and returns a new component
-   it reduces the repeatition of the code
-   `const NewComponent = higherOrderComponent(Original Component)`
-   The state variables are defined in the higherOrderComponent and passed as props to original component, if there are multiple original components being rendered through a single higher order component, each new component gets its own state variable
-   ```jsx
    const UpdatedComponent = (OriginalComponent) => {
        class NewComponent extends React.Component {
            // States and Props are accessed here
            render() {
                return <OriginalComponent props_name = props_value/>; // state is passed down to the component as prop for access
            }
        }
        return NewComponent;
    };
    import UpdatedComponent from "./UpdatedComponent";
    class Counter extends React.Component {
        //body
    }
    export default UpdatedComponent(Counter);
    ```

### 10. Render Props

-   technique for sharing code between React components using prop whose value is a function
-   If there is another type of counter like hover counter the Counter code can be shared and repeatition can be avoided
-   ```jsx
    // App.jsx
    class App extends React.Component {
        render() {
            return (
                <Counter
                    render={(count, incrementCount) => {
                        <ClickedCounter
                            count={count}
                            incrementCount={incrementCount}
                        />;
                    }}
                />
            );
        }
    }

    // Counter.jsx
    class Counter extends React.Component {
        constructor() {
            super();
            this.state = {
                count: 0,
            };
        }
        incrementCount() {
            this.state((prevState) => {
                return { count: prevState.count + 1 };
            });
        }
        render() {
            return {this.props.render(count, incrementCount)}
        }
    }
    ```

### 11. Context

-   Provides a way to pass data through the component tree without having to pass props down manually at every level
-   Create the context:
    -   ```jsx
        const userContext = React.createContext(defaultValue); // default value can be set if not provided by the userProvider
        const userProvider = userContext.Provider;
        const userConsumer = userContext.Consumer;
        export { userProvider, userConsumer };
        ```
-   Provide a context value
    -   whichever component is wrapped inside the userProvider will have access to the context
    -   ```jsx
        <userProvider value="HELLO">
            <Component>
        </userProvider>
        ```
-   Consume the context value
    -   value can only be accessed inside the userConsumer
    -   ```jsx
        <userConsumer>
            {(value) => {
                <div> {value} </div>;
            }}
        </userConsumer>
        ```
