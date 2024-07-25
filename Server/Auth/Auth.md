# Auth

### 1. Authentication

-   Authentication is the process of verifying the identity of a user, device, or entity.
-   For eg: document verifying that a person exists or not
-   Authentication is of two types
    -   StateFull: client just receive a unique key and server stores all the information about the key and client, Memory is utilised which causes delay in response [Statefull Auth](https://youtu.be/OWeruyqhiTo?si=qlGHj64O8MZ0JXcd)
    -   Stateless: client receive all the information in an encrypted way which is verified by the server to be unique and can only link to that particular client, server does not hold any data rather it just verifies the encryption it recieves upon subsequent requests, if verification failed it rejects the request [Stateless Auth](https://youtu.be/mGrVmEex6_g?si=uAge_yvfiNHGl_IA)
-   We can send this key via cookies(recommended for browsers), headers(recommended for cross-platform), response

    -   Sending tokens/keys via response:

        ```js
        //server
        res.json({ token: token });

        //client
        // client can now store this token with it and send it with subsequent requests (Note: token will not be sent automatically)

        const header = {
            token: token,
        };
        // this header is attached to every request and server will then check this header and verifies

        // or
        // this is the standard practice
        const header = {
            // Authorization: <auth-schema> <token>,
            Authorization: Bearer <token>, // Bearer is used for token authentication
        }
        ```

### 2. Authorization

-   process of determining what an authenticated user or entity is allowed to do.
-   For eg: Admin

### 3. Cookie

-   cookies are bits of information that are stored in user's browser,
-   browser will send the cookie on subsequent requests to the site, and updates the cookie if changed by the server
-   cookies can be signed to maintain its integrity
    -   a secret is maintained and inside that secret the value is added
-   `res.cookie` is used to set the cookies (key-value pair)
    ```js
    app.get(path, (req, res) => {
        res.cookie("key", "value", { signed: true });
    });
    ```
-   `cookie-parser` is a middleware which parse cookies attached to the client request object and populate the req.cook ies property with an object keyed by the cookie names.
    ```js
    const cookieParser = require("cookie-parser");
    app.use(cookieParser(#secret));
    res.cookie("attrib", "val",{signed: true});
    // cookies are added in req.cookies
    console.dir(req.cookies);
    // signed cookies are not added above instead they are added in
    console.dir(req.signedCookies);
    res.clearCookie(#cookieName);
    ```
-   cookies are domain specific

### 4. JWT

-   JWT are tokens which are stored in user's browser,
-   it helps to implement stateless authentication
-   it stores data in the payload which encrypted according to the secret
-   browser will send this token on subsequent requests to the site, and updates the token if changed by the server
-   tokens are signed to maintain its integrity
    -   a secret is maintained and inside that secret the value is added
-   Two tokens should be created:
    -   Access Token: Short Spanned (usually 15m-30m), stored in memory
    -   Refresh Token: Long Spanned (usually, 30d), stored in http-only cookie, when access token expires Refresh Token is used to create new access token

```js
// auth.js (middleware)
const jwt = require("jsonwebtoken");
const secret = "";
const setUser = (data) => {
    const payload = {
        key: value, //data
    };
    return jwt.sign(payload, secret);
};
const getUser = (token) => {
    if (!token) return null;
    try {
        return jwt.verify(token, secret);
    } catch (e) {
        return null;
    }
};

// controller
const func = (req, res, next) => {
    // body

    const token = setUser(data);
    res.cookies("uid", token);
};
```

### 5. Crypto

-   in-built library used for hashing passwords
-   it generates unique salt and hashed password for specified passwords
-   this salt and hashed password should be stored in the database since they are unique for each entry

```js
const { createHmac, randomBytes } = require("crypto");
userSchema.pre("save", function (next) {
    const user = this;
    if (!user.isModified("password")) return;
    const salt = randomBytes(16).toString();
    const hashedPassword = createHmac("sha256", salt)
        .update(user.password)
        .digest("hex");

    this.salt = salt;
    this.password = hashedPassword;
    next();
});

userSchema.static("matchedPassword", function (email, password) {
    const user = User.findOne({ email });
    if (!user) return false;

    const salt = user.salt;
    const hashedPassword = user.password;

    return (
        createHmac("sha256", salt).update(password).digest("hex") ===
        hashedPassword
    );
});
```

### 6. Bcrypt

-   used for authentication
-   hashedpassword = salt + encryptedPwd, since hashedpassword already contains salt seperately in it, there is no need of storing salt seperately
-   `const salt = await bcrypt.genSalt(12);`: async function which generates a salt or secret which will be used to hash the text
-   `const hash = await bcrypt.hash(plaintxt, salt);`: hashes the text according to the secret
-   `bcrypt.compare(pw, hashedpw)`

### 5. Session

-   Used because it is not good to store a lot of data client-side using cookies
-   Sessions are server-side data store that is used to make HTTP stateful
-   it is updated everytime a session / webpage is loaded
-   By default MemoryState is used as storage which should be used only for development and debugging purposes
    -   other session stores should be used for production

```js
const session = require("express-session");
const sessionOptions = {
    secret: "thisisasecret",
    resave: false,
    saveUninitialized: false,
};
app.use(session(sessionOptions));
```

-   **Connect-Flash** uses session and displays one time message

    ```js
    req.flash(#type, message);
    // the message is stored against the type in the session
    // and it can be accessed like
    app.get(path,(req,res)=>{
        res.render(path, {message: req.flash(type)});
    });
    // another way: By defining in the local storage using the middle flash is available to views
    app.use((req,res,next)=>{
        res.locals.messages = res.flash(type);
        next();
    })
    app.get(path,(req,res)=>{
        res.render(path, {message: req.flash(type)});
    });
    ```

-   **Connect-mongoh** creates a store in mongodb Database which will be used by session to store information
