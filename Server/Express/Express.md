# Express

### 1. [Basic Sheet](https://quickref.me/express)

```js
const express = require("express"); // imports express library
const app = express(); // create an express object
const port = 3000; // defines the port number on which server will be running
app.listen(port, callback); // Binds and listens for connections on the specified port, If port is omitted or is 0, the operating system will assign an arbitrary unused port.
app.use(path, (req, res, next) => {
    // This function is called middleware
    // if path is empty middleware will be called everytime
    // body
    // next() is used to call the next middleware
});

// In order to retrieve data from req.body we need to first parse the request object
app.use(express.urlencoded({ extended: true })); // parse form data in POST request body)
app.use(express.json()); // parse incoming JSON in POST request body)

app.set(name, value); // Assigns setting name to value.
app.set("views", path.join(__dirname, "/views")); // views directory is publically accessed by other js files, used to store static assets

// Only one response is sent per http request

app.get(path, (req, res, next) => {
    res.send(data); // res.send is used to send a response

    res.json(data); // res.send is used to send a json response

    console.log(req.headers); //used to retrieve request header
    console.log(res.setHeader(header_name, header_value)); //used to send response header
    // Always add 'X' before any custom header

    res.redirect(redirect_path); // res.redirect is used to redirect to another link
}); // catches the get requests made to the path

// Search Query: '/search?q=val'
app.get("/search", (req, res) => {
    const { q } = req.query; // query string
});

// Pattern Matching
app.get("/r/:subreddit", (req, res) => {
    const { subreddit } = req.params; // req.params: properties mapped to the named route
});

app.post(path, (req, res, next) => {
    req.body; //Contains key-value pairs of data submitted in the request body. By default, it is undefined, and is populated, it can be accessed with all routers except 'get'
}); // catches the post requests made to the path

app.use(express.static(static_path)); // It serves static files and is based on serve-static.)

// Universal: if none of the above handlers work this one will
app.all("*", (req, res, next) => {});
```

### 2. [Router](Router.md)

### 3. Method-Override

-   used to override the routing methods
-   `app.use(methodOverride("_method"))`: fakes post request to put/patch/delete request:
-   To make a put/patch/delete request:
    -   ```html
          <form method = "POST" action='api?_method=put/patch/delete>
        ```

### 4. Error Handling

-   default error status code is 500
-   we can create a custom error class on top of built-in error class
    -   ```js
        class AppError extends Error {
            constructor(status, message) {
                super();
                this.status = status;
                this.message = message;
            }
        }
        ```
-   For Ascynchronous error handling, custom errors has to be passed to the next middleware otherwise they will remain unhandled
-   if the errors are conditioned then `next(err)` should be returned otherwise the code oustide the condition will also be executed
-   asynchronous mongoose errors can be handled by `try...catch(e)`

### 5. [EJS](EJS.md)

### 6. [Mongoose](Mongoose.md)

### 7. [Multer](Multer.md)
