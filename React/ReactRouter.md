# React Router

-   handles routing in web applications. It provides a way to manage different views or pages within a single-page application (SPA) by dynamically rendering components based on the URL.
-   `npm install react-router-dom`

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { createBrowserRouter, RouterProvider } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import User from "./User";

// URL params can be sent to the loader function as an object of params
const fetchData = async ({ params }) => {
    const response = await fetch(
        "https://jsonplaceholder.typicode.com/users/1"
    );
    return response.json();
};

const addItem = async ({ request, params }) => {
    // for creating new entry
    const formData = await request.formData();
    await fetch(path, {
        method,
        //body
    });
    return null;
    // for updating data
    const formData = await request.formData();
    const updates = Object.fromEntries(formData);
    await updateContact(params.contactId, updates); // update the contact
    return redirect(redirect_path);
};

const router = createBrowserRouter([
    {
        path: "/",
        element: <Home />,
        errorElement: <ErrorPage />,
        children: [
            // To render these children element components inside the Root component <Outlet /> has to be used to define where to use this component
            {
                path: "/user/:userId",
                element: <User />, // inside the User component useParams should be imported from react-router-dom that can be used to access the userId param
                errorElement: <ErrorPage />,
                loader: fetchData, // loader is defined it is a function which loads the data
            },
        ],
    },
    {
        path: "/about",
        element: <About />,
        errorElement: <ErrorPage />,
        action: addItem,
    }, // An action is a function that runs when a form is submitted. It is used to handle form submissions and other side effects.
]);

ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
        {
            // any component outside of routing components
        }
        <RouterProvider router={router} />
    </React.StrictMode>
);

// User.jsx
import { useLoaderData } from "react-router-dom";
const User = () => {
    const data = useLoaderData();
    return <div>{data.name}</div>;
};

// About Page: Form
import { useNavigate, useSubmit, Form } from "react-router-dom";
const About = () => {
    const navigate = useNavigate();
    const submit = useSubmit();
    const handleSubmit = async (e) => {
        e.preventDefault();
        const formData = new FormData(e.target);
        await submit(formData, { method });
        navigate();
    };

    <Form method action onSubmit={handleSubmit}></Form>;
};
export default About;
```

-   all anchor tags should be changed Link tag

```jsx
import { Link } from "react-router-dom";
//reloads the page
<a href=""></a>

//does not reloads the page
<Link to=""></Link>
```

-   `<Outlet />`: component used specifically in nested route setups to render child routes within their parent route components.
