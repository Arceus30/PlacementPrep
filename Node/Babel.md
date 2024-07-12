# BABEL

-   It is a js compiler with futuristic features
-   To use Babel in a Project:-
    -   `npm init -y`
    -   install `npm i -D @babel/cli @babel/core @babel/preset-env`
    -   Create a file name "babel.config.json" and paste this
    -   ```json
        {
            "presets": ["@babel/preset-env"]
        }
        ```

### Pipeline

-   Fist install babel
-   Install the plugin: `npm i -D @babel/plugin-proposal-pipeline-operator`
-   Edit the config file, paste this:-
-   ```json
    {
        "plugins": [
            [
                "@babel/plugin-proposal-pipeline-operator",
                {
                    "topicToken": "%",
                    "proposal": "hack"
                }
            ]
        ]
    }
    ```
-   Edit the package.json file, paste this: `"start" : "babel index.js --out-file output.js && node output.js"`
-   example Code:-
    -   ```js
        let db = (x) => {
            return 2 * x;
        };
        let a = 5 |> db(%) |> db(%) |> db(%);
        console.log(a);
        ```

### prompt()

-   prompt: `prompt("Statement",def_val)`
    -   `npm init -y`
    -   install prompt-sync: `npm i prompt-sync`
    -   write the first line of your js file as: `const prompt=require("prompt-sync")();`
