# HTTP Server

#### 1. RESTful Http

**HTTP methods**

-   **GET**
    -   retrieve data
    -   req.query
-   **POST**
    -   create resource
    -   req.body
-   **DELETE**
    -   delete a resource
    -   req.query / req.body
-   **PUT**
    -   update existing resource by replacing entire resource
    -   req.body
-   **HEAD**
    -   retrieving only meta-data
-   **PATCH**
    -   Update resource (updates by updating certain part of the resource)
-   **CONNECT**
    -   establishes a tunnel to the server identified by the target resource.
-   **OPTIONS**
    -   describes the communication options for the target resource.
-   **TRACE**
    -   performs a message loop-back test along the path to the target resource.

**How response should be sent**

-   When browser is the only client then response should be sent in html format to decrease the load on the client( Server Side Rendering)
-   When anybody can be client then response (i.e, raw data) should be sent in json format (Client Side Rendering)
-   it is a recommended way to make a hybrid system in which
    -   /abc :- returns the complete html document
    -   /api/abc :- returns only the requested data

#### 2. HTTP Server And Url

-   [HTTP](https://nodejs.org/api/http.html) module is used to create and handle http servers
-   [url](https://developer.mozilla.org/en-US/docs/Web/API/URL) module is used to parse the req.url

```js
const http = require("http");
const url = require("url");

// creates server
const myServer = http.createServer((req, res) => {
    // req.url contains entire url including domain name, path, query or other parameters

    // url.parse() parses the req.url and return an object with different properties: protocol, pathName, query etc

    // parseQueryString creates an object of query string key-value pairs

    const myUrl = url.parse(req.url, { parseQueryString: true });

    // to handle different routes
    switch (myUrl.pathName) {
        case u1:
            const username = myUrl.query.username;
            break;
        case u2:
        default:
    }

    //message sent at the end to the client
    res.end(Message);
});

// server launches on portNo
myServer.listen(portNo, () => {});
```

#### 3. [Http Status Codes](https://quickref.me/http-status-code)
