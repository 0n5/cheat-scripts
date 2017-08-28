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

### Request and Response

* route handlers take in a request and response object

Request Objects:

    req.body    # contains the body of the request (POST, PUT, PATCH)
    req.path    # contains everything up to the query parameter (?)
    req.url     # contian the complete URL including the query parameters
    req.header  # contains any header in the request (GET)
    req.query   # contians the parsed query string 

Response Objects:

    res.send()         # can accept a buffer such as the body
    res.status(code)   # sets the status code
    res.json(object)   # same as send, but forces the parameter to be JSON
    

Get Request:

``` javascript

app.get('/hello', (req, res) => {
    res.send('Hello World');
});
// routes the request for /hello and responds by printing "Hello World" to screen

```

Get Request w/ Route parameter:


``` javascript

app.get('/customers:customerId', (req, res) => {
    ... // some response
});

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


### Watching / Reloading

Nodemon

    npm install -g nodemon
    nodemon ./server.js


### Middleware

* attempts to match the request URL with a file under the directory given in the function

#### express.static (only built-in middleware):

``` javascript

app.use(express.static('static'));
// will look for directory named static with a file in it

```

#### body-parser:

Installation:

    npm install body-parser

Usage:

``` javascript

const bodyparser = require('body-parser')

app.use(bodyparser.json());


```

