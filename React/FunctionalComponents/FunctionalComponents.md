# Functional Components

-   Stateless Component

### 1. Props

-   passing data from parent to child components as attributes, these are immutable `<welcome name={}/>`
-   when functions are passed as props only function definition is passed and not the function call
-   Inside a functional component, 'props' are available as an object argument.
-   JSX can be passed as children prop and can be accessed by `props.children`
-   ```jsx
    // welcome.jsx
    function welcome(props) {
        const { name } = props;
        return <h1>Hello {name}</h1>;
    }

    //Default Props
    welcome.defaultProps = {
        name: defaultValue,
    };

    // PropTypes
    welcome.propTpes = { name: PropTypes.string };

    exports default welcome

    // App.jsx
    //1st way
    <welcome name={}/>

    //2nd way
    <welcome>
    {
        // Children prop
        <p></p>
    }
    </welcome>
    ```

### 2. Memo

`export default React.memo(MyComponent)`: it checks the state and props and if there is any difference then the component will rerender otherwise not

### 3. [React-Hooks](ReactHooks.md)
