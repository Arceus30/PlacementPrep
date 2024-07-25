# File Handling

#### 1. [OS](https://nodejs.org/api/os.html)

#### 2. [Path](https://nodejs.org/api/path.html)

#### 3. [FS](https://nodejs.org/api/fs.html)

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

fs.renameSync(oldPath, newPath); //Sync renames file
fs.rename(oldPath, newPath, callback); //Async renames file

const rs = fs.createReadStream(fileName, encoding); // it creates a continuous stream so that data will be read from the file
const ws = fs.createWriteStream(fileName); // it creates a continuous stream so that data can be written in the file

rs.on("data", (chunkedData) => {
    console.log(chunkedData); // it displays data in chunk and loads next chunk once the end of this chunk is reached
    // ws.write(chunkedData) writes data in the writing stream file
});

rs.on("end", () => {
    console.log("End"); // it displays the end of file
});

rs.pipe(ws); //no memory is consumed and entire data from the reading stream is directly written inside the writing stream (file)
```

-   [File Streams](https://youtu.be/64LJJhT6Ybo?si=a8BuYi1fefTrbWV4)
