Mongo Shell
==

### Commands

    db               # prints default db (test)
    use playground   # connect to playground (another test) database
    show databases   # lists all databases 

### Collections

    show collections  # lists all collections


Insert:

    db.cats.insert({name: { first:'Inga' }, age:6 });
    # automatically creates cats collection
    # if you dont specify the id, it is pre-generated

Find:

    db.cats.find()
    # lists all objects in the cats collection

    db.cats.find().pretty()
    # formats the return objects

    db.cats.find({age:6})
    # returns cats age 6

Update:

    db.cats.update({ _id:ObjectId("599cac0dacf51357b5170045")}, { $set: { age:7 }})
    
Remove:

    db.cats.remove({"_id":ObjectId("599cac0dacf51357b5170045")})

findOne()

* returns a single document instead of a cursor to be iterated over

Indexes

* creates an index filter Mongo will use when searching

    db.employees.createIndex({age:6})

#### Operators

    $eq   # equal
    $gt   # greater than
    $gte  # greater than or equal to
    $in   # matches any values in array
    $lt   # less than
    $lte  # less than or equal to
    $ne   # not equal to
    $nin  # matches none of values in the array

Logical

    $and
    $not
    $nor  # fails to match both clauses
    $or

`db.cats.find({age: {$gte:6}})`

#### Projections

* second parameter that is passed to restrict fields in a filter

`db.cats.find({age: {$gte:6}}, age:1)`

#### Scripts

* Must initialize the default global variables, unlike the Mongo shell

```javascript
var db = new
Mongo().getDB("playground");

```    
    
Run Script

    mongo test.mongo.js