# NODEJS

-   javascript engine outside the browser, it is a runtime environment where javascript can be executed
-   WHILE SHARING: delete the node_modules folder and share the rest of the files of the project
    use `npm install` to install all the necessary dependencies
-   npm: Node Package Manager is used to manage node packages utilised by the program
-   alert(), prompt(), confirm() and DOM/UI related functions works only on browser and not in nodeJS

### Export

    -   `module.export.(var/fun)` is used to export functions,variables etc to different files which are importing this file
    -   when there's a directory full of .js files and one index.js file.
        -   index.js file imports some functions and variables from others. and exports some functions.
        -   If we import the entire directory then all the content of index will be imported and none of the other files
    -   `const exp = require("fname");`: imports file
