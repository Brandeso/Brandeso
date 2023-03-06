# Create a NodeJs project using Typescript

>Last updated on (06 / March / 2023)

The first step is to download and install NodeJs, this can be done through their official channel and [Download Links.](https://nodejs.org/en/)

Once you have Node installed, verify the instalation on your terminal

```bash
node -v
npm -v
```

1. Create the folder for your project, this can de done manually or using the `mkdir` command.

2. Once in the project folder, in the terminal run the next command, we will also install typescript library.

    ```bash
    npm init -y
    npm install --save-dev typescript
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

    Now, we will create a config file for our typescript project `tsconfig.json`

    ```json
    {
      "compilerOptions": {
        "module": "commonjs",
        "esModuleInterop": true,
        "target": "es6",
        "moduleResolution": "node",
        "sourceMap": true,
        "outDir": "dist"
      },
      "lib": ["es2015"]
    }
    ```
  
3. Once we have our project setup, we will install express and nodemon to setup a test server, we'll do that using the next command

    ```bash
    npm i -s express
    npm i --save-dev @types/express
    npm i --save-dev nodemon
    ```

4. Let's write the base file for our server, it will be inside the `dist` folder, `app.ts`

    ```typescript
    import express from 'express';
    const app = express();
    const port = 3000;

    app.get('/', (req, res) => {
      res.status(200).send('Hello World!');
    });

    app.listen(port, () => {
      return console.log(`Express is listening at http://localhost:${port}`)
    })
    ```

5. Start your server!

    For this step, we will use 2 terminal windows, on the first one run the tsc command with the `--watch` flag, this will allow the compiler to keep refreshing and compiling the files as we work on them.

    ```bash
    npx tsc --watch
    ```

    On the other terminal, we will start the server usind nodemon, this will allow us to keep the server running and updating as we work.

    ```bash
    npx nodemon dist/app.js
    ```

6. Test your server! Using Postman or your favourite web browser, go to `localhost:3000` and you will see yhe message on your get request.
