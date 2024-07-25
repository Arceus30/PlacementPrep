# DATA STRUCTURES

#### 1. Strings

-   Strings are immutable
-   **Template literals:** `let b1 = "Pramod", b2 = "Nikhil", sentence = `${b1} is a friend of ${b2}`;`
-   Strings created by new keyword is an object and is not the same as normal strings
-   `==` operator returns boolean value after comparing and `localCompare()` returns the difference in ASCII values
-   string functions
    -   `s1.length()`: returns the length of the string
    -   `s1.toUpperCase()`: returns the string converted to Upper case
    -   `s1.toLowerCase()`: returns the string converted to Lower case
    -   `s1.slice(start_ind, end_ind = end_of_string)`:it returns the string from index si to ei-1
    -   `s1.replace(searched_word,new_word)`: it returns a new string with the replaced word
    -   `s1.concat(s2)`: it concatenates two strings
    -   `s1.trim()`: it trims extra whitespaces
    -   `s1.includes(word)`: returns true if word is in the sentence and false if it is not

#### 2. Arrays

-   **Destructuring:** arrays and any other object can be destructured, `const [n1, n2, ...n] = a;`
-   `arr.toString()`: returns a string formed from the array
-   `arr.join(sep)`: it return string of the elements seperated by the seperator
-   `arr.pop()`: it removes the last element from the array and return that element
-   `arr.push(v)`: it adds that element to the end of the array and returns the length of the new array
-   `arr.shift()`: it removes first element and returns it
-   `arr.unshift()`: it add at the 0th index and returns length of the new modified array
-   `delete arr[i]`: element will be deleted but that index will contain undefined value
-   `arr1.concat(*arr2)`: it concatenates all the arrays and returns a new array
-   `arr.sort(comp)`: it sorts elements on the basis of comp, by default it sorts alphabetically (i.e, 10<2)
-   `arr.splice(start_ind,howmany,*vargs)`: it delete 'howmany' elements, add '\*vargs' elements and returns an array of deleted elements
-   `arr.slice(start_ind,ending_ind = end_of_string)`: it returns an array from index si to ei-1
-   `arr.reverse()`: it reverses the array
-   `arr.indexOf(val)`: it returns the index of first occurence of that element, if not found -1 is returned
-   `arr.includes(val)`: it will return true if element is found else return false;
-   `arr.find(test_fun)`: returns the first value that passes the test
-   `arr.findIndex(test_fun)`: returns the first index that passes the test
-   `arr.filters(filter_fun)`: it filters the array according to that `filter_fun`.
-   `arr.reduce(reducer_fun)`: it reduces the array to a single element according to that `reducer_fun`.
-   `Array.from(obj)`: it converts any other object to array
-   `array.some(fun)`: it returns true if any element passes the `fun`
-   `array.every(fun)`: it returns true if all elements passes the `fun`

#### 3. Objects

-   Accessibility: `obj[]`, `obj.`
-   `Object.keys(obj)`: it returns an array of keys of the object obj
-   Object destructuring
    ```js
    const user = { a: 1 }; // a is an attribute of the object user
    const { a } = user;
    ```
-   `this`
    -   object excuting the code or context
    -   Globally: When used outside of any function or object, this refers to the global object.(generally windows)
    -   Inside the function:
        -   Called by an object: 'this' is equal to the object
        -   Directly and not by any object: 'this' will again refer to the global object.
    -   Arrow Function :- Arrow functions do not have their own 'this' context. They inherit 'this' value from the surrounding scope (lexical scoping).
-   Prototype
    -   functions defined in prototype of an object are available to all the instances of that class
    -   prototype is an template object whereas \_\_proto\_\_ is referenece to that object
    -   when a method is defined, it is bind to an object and not to the prototype
    -   `.prototype.func`: used to add a function to the prototype of that object
