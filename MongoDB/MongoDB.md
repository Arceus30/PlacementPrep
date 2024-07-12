# MONGODB

### [Basic Sheet](https://quickref.me/mongodb)

-   It is a NoSql Database
-   it stores data in BSON format: Binary Javascript Object notaition
-   group of field value pairs is called document
-   group of document is called collection
-   group of collection is called database
-   **sorting**: db.collection.find().sort({sortingField: (1/-1) })
    -   1 for ascending order
    -   -1 for descending order
-   **limit**: db.collection.find().limit(No. of documents required)

    -   once we obtain the required no. of documents when we call the function for next set of documents first set should be skipped: db.collection.find().skip((pageNo - 1)\*No).limit(No): {it skips 'pageNo' pages and fetch next set of 'No' data}

-   `db`: database currently working on
-   `show databases / dbs`: Print a list of all available databases
-   `use db`: Set current database; if database does not exist it will create the database automatically
-   `show collections`: tables / collections inside a database
-   `drop`: delete the database
-   `db.collection.drop()`: used to delete / drop a collection
-   **Find**:

    -   `db.collection.find(query, projection, options)`: all parameters are optional, if no parameter is provided it will return entire collection
        -   projection is used to fetch specific fields: db.collection.find({query}, {projection})
    -   `db.collection.find({'directProperty.indirectProperty':value})`: if indirectProperty is nested inside of directProperty then to access indirectProperty we can use this
    -   `db.collection.findAndModify({query, update})`: Updates and returns a single document. By default, the returned document does not include the modifications made on the update. To return the document with the modifications made on the update, use the new option.
    -   `db.collection.findOne(query, projection, options)`: Returns one document that satisfies the specified query criteria.
    -   `db.collection.findOneAndDelete(filter, options)`: Deletes a single document based on the filter and sort criteria, returning the deleted document.
    -   `db.collection.findOneAndReplace(filter, replacement,options)`: Replaces a single document based on the filter and options.
    -   `db.collection.findOneAndUpdate(filter,update, options)`: Updates a single document based on the filter and sort criteria.

-   **Insert**:

    -   `db.database_name.insertOne(obj)`: it inserts one object obj in the collection of the selected database
    -   `db.database_name.insertMany([obj1,obj2])`: it inserts more than one object from an array of objects
    -   `db.database_name.bulkWrite()`

-   **Update** :-

    -   `db.database_name.updateOne(filter,update,options)`: it updates one object obj in the collection of the selected database
    -   `db.database_name.updateMany(filter, update, options)`: it updates more than one object from an array of objects
    -   `db.database_name.replaceOne()`: Replaces a single document within the collection based on the filter
        -   set: to update any value $set:{key:value} should be used
        -   date: to set date in an entry $currentDate:{key:true} should be used and date is adopted according to GMT

-   **Delete**:
    -   `db.database_name.deleteOne()`: it Deletes one object obj in the collection of the selected database
    -   `db.database_name.deleteMany({})`: used to delete everything from the collection
