Mongo Nodejs Driver
====

* All calls to the driver are asynchronous

#### Install

    npm install mongodb --save

``` javascript

const MongoClient = require('mongodb').MongoClient;

MongoClient.connect('mongodb://localhost/playground', function(err,db){
    db.collection('cats').find().toArray(function(err, docs){
        console.log(docs);
        db.close();
    })
})

// returns a cursor to iterate over
// calling toArray on the cursor makes an array out of all the documents
// calls callback when ready
// passes the docs array as a parameter to the callback
// logs the docs array

```

#### Callback Insert

``` javascript

function insertWithCallbacks() {
    MongoClient.connect('mongodb://localhost/playground', function(err, db){
        db.collection('cats').insertOne({id:1, name: 'inga'}, function(err, result){
            console.log("Result", result.insertedId);
            db.collection('cats').find({id:1}).toArray(function(err,docs){
                console.log('Result', docs);
                db.close();
            })
        })
    })
}

```

#### Promises Insert

``` javascript

function insertWithPromises() {
    let db;
    MongoClient.connect('mongodb://localhost/playground')
        .then(connection => {
            db = connection;
            return db.collection('cats').insertOne({id:1, name: 'Inga'});
      }).then(result => {
            console.log(result.inertedId);
            return db.collection('cats').find({id:1}).toArray();
      }).then(docs => {
            console.log(docs);
            db.close();
      }).catch(err=> {
          console.log('ERROR', err);
      });
}

```

#### Async module Insert

Install

    npm install async

``` javascript

function insertWithAsync() {
    const async = require('async');
    let db;
    async.waterfall([
        next => {
            MongoClient.connect('mongodb://localhost/playground', next);
        },
        (connection, next) => {
            db = connection;
            db.collection('cats').insertOne({id:1, name: 'helga'}, next);
        },
        (insertResult, next) => {
            console.log(insertResult.insertedId);
            db.collection('cats').find({id:1}).toArray(next);
        },
        (docs,next) => {
            console.log(docs);
            db.close();
            next(null, 'done');
        }
    ], (err, result) => {
        if(err)
        console.log('ERROR', err);
        else
            console.log(result);
    });
}
```

#### Express

Connection

``` javascript

const MongoClient = require('mongodb').MongoClient;
// nodejs mongo driver

let db;
MongoClient.connnect('mongodb://localhost/cats').then(connection => {
    db = connection;
    app.listen(3000, () => {
        console.log('Server started on port 3000');
    });
    // keeps connection open
}).catch(error=> {
    console.log('ERROR', error);
});

```

Get Request

``` javascript

app.get('/api/cats',(req, res) => {
    db.collection('cats').find().toArray().then(cats => {
        const metadata = { total_count: cats.length };
        res.json({_metadata:metadata, cats:cats})
    }).catch(error => {
        console.log(error);
        res.status(500).json({message: `Internal Server Error: ${error}`});
    });
});
// calls find on the collection and returns it as an array and then provides response in json format with length metadata

```


