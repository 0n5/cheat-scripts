Mongodb Basics
===

* Mongo is a schemaless document database
* Documents (Objects) are the equivalent to records in an RDBMS
* Collections are the equivalent to columns
* Primary key is managed by Mongo and uses `_id` to generate a unique key 
* Primary key data type is `ObjectId`
* Uses methods for CRUD operations
* Methods cannot operate on multiple collections at same time
* Database scales by using sharding accross multiple servers
* Encourages denormalization by using embedded documents for relations