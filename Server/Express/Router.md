# Express Router

-   We cam seperate routes of a particular type to a seperate page
-   shelterRoutes.js will handle all the paths with prefixes `/shelters`
-   ```js
    //server.js
    const shelterRoutes = require(path.../shelterRoutes);

    // if multiple routing methods(get,post,etc) have same path they can be clubbed together seperately
    app.use("/shelters", shelterRoutes);

    //shelterRoutes.js
    const express = require('express');
    const router = express.Router();

    router.get('/',(req,res)=>{});
    module.exports = router;
    ```
