title: SparkMongoCollectionReadWrite
link: https://docs.gamesparks.net/documentation/cloud-code-api/mongo-cloud-code-api/sparkmongocollectionreadwrite
author: gabriel.page
description: 
post_id: 2394
created: 2014/05/08 11:10:20
created_gmt: 2014/05/08 11:10:20
comment_status: closed
post_name: sparkmongocollectionreadwrite
status: publish
post_type: post

<!--Provides read write only access to a mongo collection. -->

# SparkMongoCollectionReadWrite

[toc] 

Provides read write only access to a mongo collection.

All methods defined in SparkMongoCollectionReadOnly are available in this object along with those listed below.

e.g.
    
    
    var myMetaCollection = Spark.runtimeCollection('metatest');

* * *

### count

**signature** count()

**returns** number

Returns the number of documents in this collection

**returns**

the number of documents

**example**
    
    
    var count = myMetaCollection.count();

* * *

**signature** count(JSON query)

**returns** number

Returns the number of documents that match the supplied query

**returns**

the number of documents

**example**
    
    
    var count = Spark.metaCollection('metatest').count({"metafield" : "metavalue"});

* * *

### distinct

**signature** distinct(string key)

**returns** JSON

Returns a list of distinct values for the given key in the collection

**params**

key - the key to use in the query

**returns**

an object array

**example**
    
    
    var keys = Spark.metaCollection('metatest').distinct("metafield");

* * *

**signature** distinct(string key, JSON query)

**returns** JSON

Returns a list of distinct values for the given key in the collection that match the supplied query

**params**

key - the key to use in the query

query - the Mongo query

**returns**

an object array

**example**
    
    
    var keys = Spark.metaCollection('metatest').distinct("metafield", {"metafield1":{"$gte" : 5}});

* * *

### dropIndex

**signature** dropIndex(JSON keys)

**returns** void

Drops or removes the specified index from a collection.

**params**

keys - the index definition used in ensureIndex.

**example**
    
    
    Spark.metaCollection('metatest').dropIndex({"metafield" : 1});

* * *

### dropIndexByName

**signature** dropIndexByName(string name)

**returns** void

Drops or removes the specified index from a collection.

**params**

name - the name of the index to drop.

**example**
    
    
    Spark.metaCollection('metatest').dropIndexByName("myIndex");

* * *

### ensureIndex

**signature** ensureIndex(JSON keys)

**returns** void

Creates an index on the specified fields if the index does not already exist.

**params**

keys - the index definition used in ensureIndex.

**example**
    
    
    Spark.metaCollection('metatest').ensureIndex({"metafield" : 1, "metafield1" : 1});

* * *

**signature** ensureIndex(JSON keys, JSON optionsIN)

**returns** void

Creates an index on the specified fields if the index does not already exist.

**params**

keys - the index definition used in ensureIndex.

optionsIN - index options

**example**
    
    
    Spark.metaCollection('metatest').ensureIndex({"metafield" : 1, "metafield1" : 1}, {"name":"myIndex"});

* * *

### find

**signature** find()

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Returns a SparkMongoCursor of all documents in this collection

**params**

**example**
    
    
    var results = Spark.metaCollection('metatest').find();

* * *

**signature** find(JSON query)

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Returns a SparkMongoCursor of all documents in this collection that match the supplied query

**params**

query - a Mongo query

**example**
    
    
    var results = Spark.metaCollection('metatest').find({"metatest1" : {"$gt" : 1}});

* * *

**signature** find(JSON query, JSON fields)

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Returns a SparkMongoCursor of all documents in this collection that match the supplied query.

The returned documents only contain the fields supplied in the fieldsToReturn parameter. This reduces the document size when being returned.

**params**

query - a Mongo query

fields - the fields to return

**example**
    
    
    var results = Spark.metaCollection('metatest').find({"metatest1" : {"$gt" : 1}}, {"metatest" : 1});

* * *

### findOne

**signature** findOne()

**returns** JSON

Returns the first document from the collection according to natural order (which reflects the order of documents on the disk)

**returns**

A JSON object

**example**
    
    
    var results = Spark.metaCollection('metatest').findOne();

* * *

**signature** findOne(JSON query)

**returns** JSON

Returns one document that satisfies the specified query criteria.

If multiple documents satisfy the query, this method returns the first document according to the natural order which reflects the order of documents on the disk.

**params**

query - a Mongo query

**example**
    
    
    var result = Spark.metaCollection('metatest').findOne({"metatest1" : {"$gt" : 1}}

* * *

**signature** findOne(JSON query, JSON fields)

**returns** JSON

Returns one document that satisfies the specified query criteria.

If multiple documents satisfy the query, this method returns the first document according to the natural order which reflects the order of documents on the disk.

The returned documents only contain the fields supplied in the fieldsToReturn parameter. This reduces the document size when being returned.

**params**

query - a Mongo query

fields - the fields to return

**example**
    
    
    var result = Spark.metaCollection('metatest').findOne({"metatest1" : {"$gt" : 1}}, {"metatest" : 1});

* * *

**signature** findOne(JSON query, JSON fields, JSON orderBy)

**returns** JSON

Returns one document that satisfies the specified query criteria.

If multiple documents satisfy the query, this method returns the first document according to the natural order which reflects the order of documents on the disk.

The returned documents only contain the fields supplied in the fieldsToReturn parameter. This reduces the document size when being returned.

**params**

query - a Mongo query

fields - the fields to return

orderBy - the order clause

**example**
    
    
    var result = Spark.metaCollection('metatest').findOne({"metatest1" : {"$gt" : 1}}, {"metatest" : 1});

* * *

### findAndModify

**signature** findAndModify(JSON query, JSON update)

**returns** JSON