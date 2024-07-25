# File Handling In Express

#### Multer

**Uses:**

-   Multer is a middleware for handling `multipart/form-data`, which is primarily used for uploading files in ExpressJS applications.

**Functions:**

-   **Disk Storage Engine**: `diskStorage` is one of the storage engines provided by Multer. It saves uploaded files directly to the disk.
    -   **Destination**: Specifies the folder where the uploaded files will be stored.
    -   **Filename**: Defines the naming convention for the uploaded files.
-   **Middleware**: Multer provides middleware functions that can be used to handle file uploads in routes.

```js
// frontend
// <form action method="POST" enctype="multipart/form-data">
//     <input type='file' name="FILENAME">
//     <button type="submit">Upload</button>
// </form>

// backend
const multer = require("multer");

// to handle disk storage better
const storage = multer.diskStorage({
    destination: (req, file, cb) => {
        // cb(error, destination)
        cb(null, "./uploads");
    },
    filename: (req, file, cb) => {
        const uniqueSuffix = Date.now() + "-" + Math.round(Math.random() * 1e9);
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

#### Cloudinary

**Uses:**

-   Cloudinary is a cloud-based service that provides an end-to-end image and video management solution.
-   It offers tools for uploading, storing, managing, manipulating, and delivering images and videos.

**Functions:**

-   **Upload**: Allows users to upload media files directly to Cloudinary's cloud storage.
-   **Storage**: Provides secure and scalable storage for media files.
-   **Transformation**: Offers powerful transformation capabilities for resizing, cropping, adjusting image quality, adding overlays, and more.
-   **Delivery**: Provides fast delivery of media files through a content delivery network (CDN), ensuring quick load times for end-users.
-   **Management**: Offers a comprehensive dashboard for managing and organizing media assets.

-   used inside function
    ```js
    const result = await cloudinary.uploader.upload(imageUrl, {
        folder: "yelpCampSeed",
    });
    ```

```js
// cloudinary_config.js
const cloudinary = require("cloudinary").v2;
const { CloudinaryStorage } = require("multer-storage-cloudinary"); //

// cloudinary setup
cloudinary.config({
    cloud_name: process.env.CLOUDINARY_CLOUD_NAME,
    api_key: process.env.CLOUDINARY_KEY,
    api_secret: process.env.CLOUDINARY_SECRET,
});

module.exports = {
    cloudinary,
};
```

#### Multer-Storage-Cloudinary

**Uses**

-   multer-storage-cloudinary is a storage engine for Multer to directly upload files to Cloudinary.

**Functions**:

-   Configuration: Requires Cloudinary credentials and configuration settings to authenticate and specify upload behavior.
-   Transformation Options: Allows setting options for Cloudinary transformations during the upload process.

```js
const multer = require("multer");
const { CloudinaryStorage } = require("multer-storage-cloudinary");
const cloudinary = require("cloudinary").v2;

cloudinary.config({
    cloud_name: "your_cloud_name",
    api_key: "your_api_key",
    api_secret: "your_api_secret",
});

const storage = new CloudinaryStorage({
    cloudinary: cloudinary,
    params: {
        folder: "uploads",
        format: async (req, file) => "png", // supports promises as well
        public_id: (req, file) => "computed-filename-using-request",
    },
});

const upload = multer({ storage: storage });

app.post("/upload", upload.single("file"), (req, res) => {
    res.send("File uploaded to Cloudinary successfully!");
});
```
