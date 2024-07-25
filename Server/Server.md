# Server

#### 1. MVC

**Model View Controller**

-   Components of MVC:
    -   Model: It manages the data and provides it to the View component.
    -   View: Responsible for rendering the user interface (UI) and displaying the data provided by the Model.
    -   Controller: Acts as an intermediary between the Model and View, handling user input, processing data, and updating the View accordingly.

#### 2. [Nodemon](https://nodemon.io/)

#### 3. [dotenv](https://github.com/motdotla/dotenv#readme)

```js
if (process.env.NODE_ENV !== "production") require("dotenv").config();
```

#### 4. [Cors](https://github.com/expressjs/cors#readme)

-   Cors need to be setup for cross origin access

#### 4. [HTTP Server](HTTP%20Server/HTTPServer.md)

#### 5. [Express](Express/Express.md)

**Note**:

-   In order to prevent race condition we should abort any pending requests first and then send a new request from frontend to server

#### 6. [XMLHTTP Request](XMLHTTP/XMLHTTP.md)

#### 7. [Fetch](Fetch/Fetch.md)

#### 8. [Axios](Axios/Axios.md)

#### 9. [Auth](Auth/Auth.md)

#### 10. [WebSockets](WebSocket/WebSocket.md)

#### 11. [Clustering](https://youtu.be/JoPZ9gEvpz8?si=c_YBpWBMhvu7aOYE)
