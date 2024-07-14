# MongoDB

### 1. [Basic Sheet](https://quickref.me/mongodb)

-   It is a NoSql Database
-   it stores data in BSON format: Binary Javascript Object notaition
-   group of field value pairs is called document
-   group of document is called collection
-   group of collection is called database

**Use mongoDB atlas for deployed database**

### 2. Sorting

-   `db.collection.find().sort({sortingOrder: (1/-1) })`
    -   1 for ascending order
    -   -1 for descending order

### 3. limit

-   `db.collection.find().limit(n)` n=no. of documents required
-   `db.collection.find().skip((pageNo - 1)\*n).limit(n)` it skips 'pageNo' pages and fetch next set of 'n' data

### 4. Find

-   `db.collection.find(query, projection, options)`: if no parameter is provided it will return entire collection - projection is used to fetch specific fields: db.collection.find({query}, {projection})
-   `db.collection.find({'directProperty.indirectProperty':value})`: if indirectProperty is nested inside of directProperty
-   `db.collection.findOne(query, projection, options)`: Returns one document.

### 5. Insert

-   `db.database_name.insertOne(obj)`: it inserts one object in the collection
-   `db.database_name.insertMany([obj1,obj2])`: it inserts more than one object from an array of objects

### 6. Update

-   `db.database_name.updateOne(filter,update,options)`: it updates one object
-   `db.database_name.updateMany(filter, update, options)`: it updates more than one object from an array of objects
-   `db.database_name.replaceOne()`: Replaces a single document within the collection

-   `db.collection.findAndModify({query, update})`: Updates and returns a single document. To return the document with the modifications made on the update, use `{new:true}`.
-   `db.collection.findOneAndReplace(filter, replacement,options)`: Replaces a single document based on the filter and options.
-   `db.collection.findOneAndUpdate(filter,update, options)`: Updates a single document based on the filter and sort criteria.

    -   set: to update any value $set:{key:value} should be used
    -   date: to set date in an entry $currentDate:{key:true} should be used and date is adopted according to GMT

### 7. Delete

-   `db.database_name.deleteOne()`: it Deletes one object obj in the collection of the selected database
-   `db.database_name.deleteMany({})`: used to delete everything from the collection
-   `db.collection.findOneAndDelete(filter, options)`: Deletes a single document based on the filter and sort criteria, returning the deleted document.
