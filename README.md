# Exercise (Instructions): Node and MongoDB

## Part 1

### Objectives and Outcomes

In this exercise you will install the Node MongoDB driver module and configure your Node application to communicate with the MongoDB server. At the end of this exercise, you will be able to:

Install and use the Node MongoDB driver
Interact with the MongoDB database from a Node application
Installing the Node MongoDB Driver Module

Create a new folder named node-mongodb and move into the folder.
Install the Node MongoDB driver and the Assert module by typing the following at the prompt:
```
     npm install mongodb --save
npm install assert --save
```
A Simple Node-MongoDB Application

Create a new file named `simpleserver.js` and add the following code to it:
```
var MongoClient = require('mongodb').MongoClient,
    assert = require('assert');

// Connection URL
var url = 'mongodb://localhost:27017/conFusion';
// Use connect method to connect to the Server
MongoClient.connect(url, function (err, db) {
    assert.equal(err,null);
    console.log("Connected correctly to server");
        var collection = db.collection("dishes");
        collection.insertOne({name: "Uthapizza", description: "test"}, function(err,result){
        assert.equal(err,null);
        console.log("After Insert:");
        console.log(result.ops);
                collection.find({}).toArray(function(err,docs){
            assert.equal(err,null);
            console.log("Found:");
            console.log(docs);
                        db.dropCollection("dishes", function(err, result){
               assert.equal(err,null);
               db.close();
            });
        });
            });
});
```

Make sure that your MongoDB server is up and running
Type the following at the prompt to start the server and see the result.
     `node simpleserver`

### Conclusions

In this exercise you installed the Node MongoDB driver and used it to communicate with the MongoDB server from a Node application.
