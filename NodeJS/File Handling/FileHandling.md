# File Handling

### 1. 'os' and 'path' module

-   used when working with operating system and directories and file paths
-   ```js
    const os = require("os");
    const path = require("path");

    console.log(os.type()); // prints the type of the operating system
    console.log(os.version()); // prints the version of the operating system
    console.log(os.homedir()); // prints the current working directory

    console.log(__dirname); /* prints the path to the directory of the file*/
    console.log(__filename); /* prints the path to the file*/

    path.dirname(filename); /*returns the path to the directory of the file*/
    path.basename(filename); /*returns the name of the file with extension*/
    path.extname(filename); /*returns the extension of the file*/
    path.parse(filename); /*returns a object with all the file information*/
    path.join(d1, d2, d3); /*joins multiple paths into one*/
    ```

### 2. 'fs' module

-   used for file handling
-   ```js
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

    fs.rename(oldPath, newPath, callback); //Async renames file
    fs.renameSync(oldPath, newPath); //Sync renames file

    const rs = fs.createReadStream(fileName, encoding); // it creates a continuous stream so that data will be read from the file
    const ws = fs.createWriteStream(fileName); // it creates a continuous stream so that data can be written in the file

    rs.on("data", (chunkedData) => {
        console.log(chunkedData); // it displays data in chunk and loads next chunk once the end of this chunk is reached
        // ws.write(chunkedData) writes data in the writing stream file
    });

    rs.on("enc", () => {
        console.log("End"); // it displays the end of file
    });

    rs.pipe(ws); //no memory is consumed and entire data from the reading stream is directly written inside the writing stream (file)
    ```

-   [Streams](https://youtu.be/64LJJhT6Ybo?si=a8BuYi1fefTrbWV4)
-   Apart from sync/async versions we can also to use promises version to prevent callback hell
