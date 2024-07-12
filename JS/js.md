<a href="https://quickref.me/javascript">Basic Sheet</a>

**typeCasting**

1. String to Number: Number.parseInt();
2. String to float: Number.parseFloat();

**var let const**
![](https://imgs.search.brave.com/I668U4U6VK3Ix8X5_SB3fi5ZCHpM3UF553fPAb7YtQk/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tZWRp/YS5saWNkbi5jb20v/ZG1zL2ltYWdlL0Q1/NjEyQVFHWkxLalNa/T3pBZ2cvYXJ0aWNs/ZS1jb3Zlcl9pbWFn/ZS1zaHJpbmtfNjAw/XzIwMDAvMC8xNjg3/ODMwMDEwMDkzP2U9/MjE0NzQ4MzY0NyZ2/PWJldGEmdD1KOTR1/VUxiQWVMTE1YdHRt/bU9SeTU5TGszZzNL/MUlIQUUyNjNpMVFH/SG00)

<a href="https://quickref.me/json">JSON Basic Sheet</a>

<a href="https://youtu.be/EfAl9bwzVZk?t=19267&si=3aROn8Zc3koCM9XV">Web Storage API</a>

**Currying**

-   a function with multiple arguments is transformed into a sequence of nested functions, each taking a single argument. This allows to partially apply the function to some arguments and delay the application of the rest until later.
-   ```js
    const sendEmail = (to) => (subject) => (body) =>
        console.log(to, subject, body);
    //or
    function sendEmail(to) {
        return function (subject) {
            return function (body) {
                console.log(to, subject, body);
            };
        };
    }

    const step1 = sendEmail("TO");
    const step2 = step1("SUBJECT");
    step2("BODY");
    ```
