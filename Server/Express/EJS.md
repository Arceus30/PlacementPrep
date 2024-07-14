# Ejs

### 1. [Basic Sheet](https://quickref.me/ejs)

-   Server Side Rendering
-   simple templating language which can help to write html with js
-   `<%= %>`: used to write javascript
-   `<%- %>`: used to include any ejs file (generally the file included is called partial)
    -   ```js
        // Inside the server, view engine need to be set to use ejs
        app.set("view engine", "ejs"); // for ejs templating
        app.set("views", path.join(_dirname, "views")); // sets the location of the views directory which stores the ejs files
        app.get(path, (req, res) => {
            res.render("home.ejs"); // render a view and sends the rendered HTML string to the client.
        }); //home.ejs is saved in the public directory views can be accessed from anywhere
        ```
-   When data is passed from server to ejs it is stored inside 'locals'
