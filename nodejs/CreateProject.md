# Create a NodeJs project

>Last updated on (15 / February / 2023)

The first step is to download and install NodeJs, this can be done through their official channel and [Download Links.](https://nodejs.org/en/)

Once you have Node installed, verify the instalation on your terminal.

```bash
node -v
npm -v
```

1. Create the folder for your project, this can de done manually or using the `mkdir` command.

2. Once in the project folder, in the terminal run the next command.

    ```bash
    npm init
    ```

    Here, it will ask for the next information:

    ```bash
    package name: (simple-node-server)
    version: (1.0.0)
    description:
    entry point: (index.js)
    test command:
    git repository:
    keywords:
    author:
    license: (ISC)
    ```

    These will create  a `package.json` file, this is the file that will contain all the information, packages and setup for your project.
  
3. Once we have our project setup, we will install express to setup a test server, we'll do that using the next command.

    ```bash
    npm i -s express
    ```

4. Let's write the base file for our server, in the file `index.js`.

    ```javascript
    const express = require('express');
    const app = express();
    const port = 3000;

    app.get('/', (req, res) => {
        res.status(200).send(`Hello World! Listening on port: ${port}`);
    })

    app.listen(port, () => {
        console.log(`Now listening on port ${port}`);
    })
    ```

5. Start your server!

    ```bash
    node index.js
    ```

6. Test your server! Using Postman or your favourite web browser, go to `localhost:3000` and you will see yhe message on your get request.
