Express Configuration
==


### Create Server

In project root along side package.json file:

    nano server.js

``` javascript

const express = require('express');
// import express module

const app = express()
// instantiates express

app.listen(8000, () => {
    console.log('Server starting / running on port 8000')
});
// specifies the port express should run on

```


### Watching / Reloading

Nodemon

    npm install -g nodemon
    nodemon ./server.js


### Middleware

Static content

``` javascript

app.use(express.static('static'));

```

Parse JSON Post Requests

Install body-parser:

    npm install body-parser

Usage:

``` javascript

const bodyparser = require('body-parser')

app.use(bodyparser.json());


```


### Requests


Get Request:

``` javascript

app.get('/hello', (req, res) => {
    res.send('Hello World');
});
// routes the request for /hello and responds by printing "Hello World" to screen

```

Post Request:

``` javascript

app.post('/posts', (req, res) => {
  res.send('Got a POST request')
});

```

Delete Request:

``` javascript

app.delete('/posts', (req, res) => {
  res.send('Got a Delete request')
});

```

Update Request:

``` javascript

app.put('/posts', (req, res) => {
  res.send('Got an Update request')
});

```
