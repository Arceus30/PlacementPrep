# Multer

-   library used for handling files at server (files input, upload, retrieve etc)
-   `enctype="multipart/form-data"` is used to upload the files from form input
-   ```js
    // frontend
    // <form action method="POST" enctype="multipart/form-data">
    //     <input type='file' name="FILENAME">
    //     <button type="submit">Upload</button>
    // </form>

    // backend
    const multer = require("multer");

    const { upload } = multer({ dest: "/uploads" }); // destination can be anywhere we want images to be stored

    // to handle disk storage better
    const storage = multer.diskStorage({
        destination: (req, file, cb) => {
            // cb(error, destination)
            cb(null, "./uploads");
        },
        filename: (req, file, cb) => {
            const uniqueSuffix =
                Date.now() + "-" + Math.round(Math.random() * 1e9);
            // cb(error, fileName)
            cb(null, file.fieldname + "-" + uniqueSuffix);
        },
    });

    const { upload } = multer({ storage });

    app.post(path, upload.single("FILENAME"), (req, res, next) => {});
    // upload.single(FILEName) used to upload a single image
    // upload.array(FILEArray, no. of images to be uploaded) used to upload multiple images

    // after uploading files in the destination, multer breaks the req in two parts
    // req.body consisting all the text data
    // req.file consisting all the file data
    ```
