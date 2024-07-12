**MongoDB**
<a href="https://quickref.me/mongodb">Basic Sheet</a>

-   It is a NoSql Database
-   it stores data in BSON format: Binary Javascript Object notaition

    -   group of field value pairs is called document
    -   group of document is called collection
    -   group of collection is called database

-   sorting: db.collection.find().sort({sortingField: (1/-1) })
    -   1 for ascending order
    -   -1 for descending order
-   limit: db.collection.find().limit(No. of documents required)
    -   once we obtain the required no. of documents when we call the function for next set of documents first set should be skipped: db.collection.find().skip((pageNo - 1)\*No).limit(No): {it skips 'pageNo' pages and fetch next set of 'No' data}
-   projection is used to fetch specific fields: db.collection.find({query}, {projection})
