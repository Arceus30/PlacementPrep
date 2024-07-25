# JS

#### 1. [Basic Sheet](https://quickref.me/javascript)

#### 2. [DataTypes (W3Schools)](https://www.w3schools.com/js/js_datatypes.asp)

-   **Type Conversion**
    -   `Number(a)`: it converts any datatype to Number
    -   `ParseInt(a)` : it extracts the numnber from the string and if not possible it will return NaN.
    -   `String(a)`: it converts any datatype to string
    -   `boolean(a)`: it converts any datatype to boolean, it assumes 0 as false and any other integer as true

#### 3. var let const

![](https://imgs.search.brave.com/I668U4U6VK3Ix8X5_SB3fi5ZCHpM3UF553fPAb7YtQk/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tZWRp/YS5saWNkbi5jb20v/ZG1zL2ltYWdlL0Q1/NjEyQVFHWkxLalNa/T3pBZ2cvYXJ0aWNs/ZS1jb3Zlcl9pbWFn/ZS1zaHJpbmtfNjAw/XzIwMDAvMC8xNjg3/ODMwMDEwMDkzP2U9/MjE0NzQ4MzY0NyZ2/PWJldGEmdD1KOTR1/VUxiQWVMTE1YdHRt/bU9SeTU5TGszZzNL/MUlIQUUyNjNpMVFH/SG00)

#### 4. Functions

-   The spread (...arr) syntax allows an iterable to be expanded in places where function calls (zero or more arguments) or array literals (elements) are expected
-   `process.argv`: returns an array containing the command-line arguments.
-   all the arguements which are passed with function calling are stored in arguements(array-like) object
-   Function Types

    -   Regular Function: `function fun(x) {//body}`
    -   function expression: `let square = function (number) {//body};`
    -   Arrow Function: `let sum = (a, b) => {//body};`
    -   Methods: functions defined inside the obects
    -   Higher Order Functions: Functions can take another function as input or return a function, the function taken as input is called callback

        ```js
        function makeMysteryfunc(func) {
            return function () {
                console.log("Hello");
                func();
            };
        }

        const f1 = makeMysteryfunc(func);
        f1();
        ```

#### 5. Callbacks

-   Functions passed as arguement to other function: `const calculate = (a, b, func) => {//body};`

#### 6. [Promises (W3School)](https://www.w3schools.com/js/js_promise.asp)

-   can chain multiple asynchronous operations together using .then() methods, making the code more readable and avoiding "callback hell".

#### 7. [Async-Await (W3School)](https://www.w3schools.com/js/js_async.asp)

-   Error inside async function can be handled by try...catch()

#### 8. Currying

-   a function with multiple arguments is transformed into a sequence of nested functions, each taking a single argument. This allows to partially apply the function to some arguments and delay the application of the rest until later.

```js
const sendEmail = (to) => (subject) => (body) => console.log(to, subject, body);

const step1 = sendEmail("TO");
const step2 = step1("SUBJECT");
step2("BODY");
```

#### 9. Error Handling

`try...catch`
`try...catch...finally`
we can throw custom Errors from the try block: `try { throw new Error();}`

#### 10. [JSON ](https://quickref.me/json)

-   Javascript Object Notation
-   `obj = JSON.parse(json)`: converts json string into js object
-   `JSON.stringify(obj)`: converts js object into a string of json
-   Data Representation Format
-   Commonly used for APIs and Configs

#### 11. [DOM (W3School) ](https://www.w3schools.com/js/js_htmldom.asp)

-   DOM: Document Object Model
-   Selection

    -   `document.getElementbyID()`: it returns the html element with specified id
    -   `document.getElementsByTagName()`: it returns the html collection with the given tagname
    -   `document.getElementsByClassName()`: it also returns the html collection with the given class
    -   `document.querySelector()`: it returns the first match object
    -   `document.queryselectorall()`: it returns list of objects with the same css selector

-   HTML Editor
    -   node includes text and any other thing which is not an element
    -   `dom.innerText()`: it returns all the text seen on the screen by the user
    -   `dom.textContext()`: it returns all the text in that object
    -   `dom.innerHTML()`: it returns object including tags,
        any changes including the tags will be reflected if innerHTML() is used but not be reflected if innertext() or textcontext() is used
    -   `dom.getAttribute()`: used to get the specified attribute
    -   `dom.setAttribute()`: used to add a new or change existing attribute
    -   `dom.style.property`: is used to change and add inline the css property of a tag
    -   `window.getComputedStyle(tag_object)`: it returns an object containing all the computed styles for the selected element object
    -   `dom.classList`: we can create classes and add them using classList
    -   `dom.parentElement`: it returns parent element
    -   `dom.ChildElementCount`: returns number of child elements
    -   `dom.children`: returns all the children of that tag
    -   `dom.previousElementSibling` and `dom.nextElementSibling`: returns previous or next sibling element
    -   `dom.previousSibling` and `dom.nextSibling`: returns previous or next sibling node
    -   `dom.CreateElement()`: it creates a new element
    -   `dom.AppendChild()`: it appends specified child object in specified section
    -   `dom.Append()`: inserts a set of node objects
    -   `dom.Prepend()`: inserts a set of node objects at the begininig of the child list of that tag
    -   `dom.InsertAdjacentElement(pos,ele)`: inserts an element adjacent to that element
        pos:
        -   'beforebegin': Before the targetElement itself.
        -   'afterbegin': Just inside the targetElement, before its first child.
        -   'beforeend': Just inside the targetElement, after its last child.
        -   'afterend': After the targetElement itself.
    -   `dom.after()`: inserts an element after another element
    -   `dom.Remove()`: it deletes the specified child of the parent
    -   `dom.RemoveChild()`: it deletes the specified child of the parent(but only if it is Node object)
-   Events

    -   Events are like actions related to the tags and elements for example onclick etc
    -   when events are triggered an event object is created and passed to the function

    ```js
    const btn = document.querySelector("#v2");
    btn.onclick = function (evt) {
        console.log(evt);
    };
    ```

    -   `dom.addEventListener('action',Function)`: sets up the function to the action specified of that element
    -   if any event is to be connected not to any element we can attach it to global event window
    -   Value inside an input box is accessed by input.value
    -   In case of forms `evt.preventDefault()` is used to change the default actions of the forms
    -   Event Bubbling: when an event is triggered by a nested element the trigerr propogates upward untill the root element is reached or propogation is stopped by `e.stopPropagation();`
    -   Event Delegation: an event listener is attached to the parent element and event bubbling is used to handle the events that occur inside the parent element

#### 12. [Web (local and session) Storage API (Youtube)](https://youtu.be/EfAl9bwzVZk?t=19267&si=3aROn8Zc3koCM9XV)

#### 13. [Data Structures](Data%20Structures/DataStructures.md)

#### 14. [Oops](Oops/Oops.md)
