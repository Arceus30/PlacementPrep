# XMLHttp request

-   oldest and least useful
-   uses callback and no support of promises
-   ```js
    const req = new XMLHttpRequest(); //The constructor initializes an XMLHttpRequest. It must be called before any other method calls.

    req.onload = function () {
        const d = JSON.parse(this.responseText);
        console.log("Response", d.name, d.height);
    }; // Fired when the request completes successfully

    req.onerror = function () {
        console.log("Error: ", this);
    }; // Fired when the request encountered an error

    req.open("GET", "https://swapi.dev/api/people/1/"); //initializes a request

    req.send(); // request is sent
    ```
