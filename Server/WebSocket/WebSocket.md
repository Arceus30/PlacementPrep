# WebSocket

-   For an application like chat room app where the server should send data to the client whenever it recieves its respective data, there are two options:

    -   **Pooling**: In pooling, all the clients keep sending request at specified time intervals. if the server has the data for a client it sends it to it otherwise it rejects the request or send a 'no data' response. It increases the load on the server as all the clients keep on sending requests all the time half-duplex communication server can only send response when client requests
    -   **WebSockets**: client request the server to convert its HTTP request to a websocket connection which is kept open throughout until one of them forces the connection to be closed. Server and client can send response and request whenever they like. full duplex communication

-   'socket.io' module is used

```
/* frontend: in the frontend part we need to add a script */
<script src="/socket.io/socket.io.js"></script>
<script>
    const socket = io();
    const messageInput, btn;
    socket.on('message_from_server',(message)=>{
        console.log(message);
    })
    btn.addEventListener('click',(e)=>{
        const message = messageInput.value
        socket.emit('msg', message);
    })
</script>
```

-   ```js
    // server.js
    const express = require("express");
    const { createServer } = require("http");
    const { Server } = require("socket.io");

    const app = express();
    const server = createServer(app);
    const io = new Server(server);

    io.on("connection", (socket /*client*/) => {
        console.log("connected", socket.id);
        socket.on("msg", (message) => {
            console.log(message);
            io.emit("msg_from_server", message);
        });

        socket.on("disconnect", () => {
            console.log("user disconnected");
        });
    });

    const port = 8000;
    server.listen(port, () => {});
    ```
