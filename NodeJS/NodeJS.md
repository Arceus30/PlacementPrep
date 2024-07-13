# NodeJS

-   WHILE SHARING: delete the node_modules folder and share the rest of the files of the project
-   use `npm install` to install all the necessary dependencies
-   npm: Node Package Manager is used to manage node packages utilised by the program
-   DOM/UI related functions like alert(), prompt(), etc works only in browser and not in nodeJS
-   Sync methods are blocking operations and Async methods are non-blocking operations
    -   Blocking requests / operations blocks the thread and stop execution if all available threads are blocked
    -   Non-blocling requests / operations does not blocks the thread

### 1. Export

-   Two ways of exporting and importing other files
-   **First**:

    -   ```js
        // EXPORTING
        function f1() {}
        function f2() {}
        module.exports = { f1, f2 };

        //or
        module.exports.f3 = () => {};

        // IMPORTING
        const { f1, f2, f3 } = require(fileName);
        ```

-   **Second**

    -   ```js
        // EXPORTING
        function f1() {}
        function f2() {}
        export const { f1, f2 }; /*named Exports*/

        //or
        const f3 = () => {};
        export default f3; /* default exports*/


        // IMPORTING
        import {f1,f2} from fileName /* named exports*/
        import f3 from fileName /* default exports*/

        ```

### 2. [File Handling](File%20Handling/FileHandling.md)

### 3. [HTTP Server](HTTP%20Server/HTTPServer.md)

### 4. [Babel (for futuristic features)](Babel/Babel.md)
