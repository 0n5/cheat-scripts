Express Configuration
==


### Create Server

In project root along side package.json file:

    touch server.js

``` javascript

const express = require('express');
// import express module

const app = express();
// instantiate the app

app.use(express.static('static'));
// middleware for static content

app.listen(8000, () => {
    console.log('Server starting / running on port 8000')
});
// specifies the port express should run on

```


### Watching / Reloading

Nodemon

    npm install -g nodemon
    nodemon ./server.js

