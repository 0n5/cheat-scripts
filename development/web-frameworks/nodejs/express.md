Express
=======

Requires Nodejs

#### Installation 

    npm install express 


#### Create RESTful API

create server.js in root and add:

```javascript

var express = required('express'),
    app = express();
    

app.use(express.static(__dirname + '/'));


app.get('/names/:id', function(req,res){
    var namesId = parseInt(req.params.id);
    var data = {};
    for (var i=0, len = names.length; i<len; i++) {
        if (names[i].id === namesId) {
            data = names[i];
            break;
        }
    }
    res.json(data);
});

app.get('/names', function(req,res) {
   res.json(names); 
    /*
    to test error messages comment above response out and use:
    res.json(500, { error: 'Some error message'});
    
    */
});

app.listen(8080);

console.log('express running on port 8080');


// test array for API integration

var names = [
    {
        id: 1,
        name: 'Person A'
    },
    {
        id: 2,
        name: 'Person B'
    }
]



```


#### Run Server

    node server.js