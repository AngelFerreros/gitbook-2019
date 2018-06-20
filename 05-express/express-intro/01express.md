# First Express App with Routes

To create a web application using Node, we're going to import a web app server framework called Express. We can install this as a package using npm, then use it to create applications.

---

## Setting up a project
Create a new folder for use with the project using `mkdir node_calculator`, and cd into `cd node_calculator`

First we want to start a new project by going `npm init`. Follow the instructions, clicking `enter` through the statements. you many want to specify a version number, but most default options should be fine. It will also specify an initial file to use. The default is `index.js`, and this acts as the "entry point" into our app.

---

## Basic Express Setup

Before we do anything else, let's set up a basic Express app. We need to install our dependencies, create the index.js server file, and create an index for our homepage.

```bash
npm install express
touch index.js
```

**Note:** 

We've been running `npm install -g <package name>`to install the package globally. You'll want to reserve `-g` for packages that will be run in the command line.

---

### index.js

The following example shows how to get routes working in Node. A **route** is a combination of a URL pattern + HTTP Verb (get, post, put, delete). These verbs represent a method for the request.

Each route is called on our Express app, and takes a URL pattern and a callback function. The callback function gives us back the request (`req`) and response to send back to the client (`res`). Calling the `.send` function on the response sends a string back to the client.

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('hello brian')
});

app.listen(3000)
```

---

### Installing nodemon
```bash
npm install -g nodemon
```

If we just ran `node nameOfFile.js`, node will not update if we make changes to the file. Nodemon solves this problem by updating the file once changes have been made. Install nodemon (only have to do this once), we will run our apps using the syntax

```bash
nodemon nameOfFile.js
```
