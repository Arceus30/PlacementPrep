# OOPS

### Class

-   ```js
    // user defined class whose objects can be created
    class A {
        constructor(args) {} // Constructor initialises the object
    }
    ```
-   **Extends and Super**
    -   The extends keyword is used to create a subclass that inherits from another class (parent class).
    -   It sets up the prototype chain, allowing the subclass to inherit properties and methods from the parent class.
    -   Inside the constructor of a subclass, the super() function is used to call the constructor of its parent class.
