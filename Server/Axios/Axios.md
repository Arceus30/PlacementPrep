# Axios

-   Axios is a popular JavaScript library used for making HTTP requests

```js
const getStarWarsPerson = async (id) => {
    try {
        const res = await axios.get(`https://swapi.dev/api/people/${id}/`); //get request
        console.log("Response: ", res.data);
    } catch (e) {
        console.log(e);
    }
};
const res = await axios.post(`https://swapi.dev/api/people/${id}/`, {
    key: value,
}); // post request

// we can create an object config to edit the headers values
// Eg:
const config = { headers: { Accept: "application/json" } };
const res = await axios.get(`https://swapi.dev/api/people/${id}/`, config);
```
