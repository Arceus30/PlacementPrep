# File Handling

'fs' module is used for file handling

```js
const fs = require("fs");

fs.writeFileSync(fileName, content); //Sync
fs.writeFile(fileName, content, errCallback); //Async
// a file will be created and content will be written inside
// if a file already exist, all its data will be replaced by content

const res = fs.readFileSync(fileName, encoding); //Sync
fs.readFileSync(fileName, encoding, (err, result) => {}); //Async

// Async methods does not return anything and required an error callback

fs.appendFileSync(fileName, content); //Sync
fs.appendFile(fileName, content, errCallback); //Async
// append adds content to the end of the file, without replacing
```
