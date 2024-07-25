# Fetch Request

-   it fetch data from the server and return a promise which is then resolved to resposnse

```js
fetch("https://swapi.dev/api/people/2/") // fetch a resource.
    .then((res) => {
        console.log("Response: ", res);
        return res.json(); //parse the response body as JSON
    })
    .then((d) => {
        console.log("Data: ", d);
    })
    .catch((e) => {
        console.log("Error: ", e);
    });

// To send another type of request
// Set up options for the fetch request and pass as an argument to fetch().
const options = {
    method: "POST",
    headers: {
        "Content-Type": "application/json", // Set content type to JSON
    },
    body: JSON.stringify(jsonData), // Convert JSON data to a string and set it as the request body
};
fetch("https://swapi.dev/api/people/2/", options);

// we can abort a fetch request if it takes too much time
const controller = new AbortController();
const signal = controller.signal;
fetch("https://swapi.dev/api/people/2/", { signal });

// Timeout after 5 seconds
const timeoutId = setTimeout(() => {
    controller.abort(); // Abort the fetch request
    console.log("Fetch request timed out");
}, 5000);

// Handle the fetch request
fetchPromise.then((response) => {
    // Check if the request was successful
    if (!response.ok) {
        throw new Error("Network response was not ok");
    }
    // Parse the response as JSON
    return response.json();
});
```
