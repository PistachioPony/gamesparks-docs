title: SparkMongoCursor
link: https://docs.gamesparks.net/documentation/cloud-code-api/mongo-cloud-code-api/sparkmongocursor
author: gabriel.page
description: 
post_id: 2395
created: 2014/05/08 11:10:20
created_gmt: 2014/05/08 11:10:20
comment_status: closed
post_name: sparkmongocursor
status: publish
post_type: post

<!--An iterator over database results. Doing a find() query on a collection returns a SparkMongoCursor thus: -->

# SparkMongoCursor

[toc] 

An iterator over database results. Doing a find() query on a collection returns a SparkMongoCursor thus:
    
    
    var cursor = collection.find( query );if( cursor.hasNext() ) {var obj = cursor.next();}

Warning: Calling toArray() on a SparkMongoCursor will irrevocably turn it into an array. This means that, if the cursor was iterating over ten million results (which it was lazily fetching from the database), suddenly there will be a ten-million element array in memory. Before converting to an array, make sure that there are a reasonable number of results using skip() and limit().

For example, to get an array of the 1000-1100th elements of a cursor, use
    
    
    var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();

e.g.
    
    
    var myMetaCollection = Spark.runtimeCollection('metatest');

* * *

### limit

**signature** limit(number count)

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Limits the number of elements returned.

**params**

count - the limit to set

**example**
    
    
    var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();

* * *

### skip

**signature** skip(number count)

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Discards a given number of elements at the beginning of the cursor.

**params**

count - the limit to set

**example**
    
    
    var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();

* * *

### size

**signature** size()

**returns** number

Counts the number of objects matching the query this does take limit/skip into consideration.

**example**
    
    
    var size = collection.find( query ).size();

* * *

### count

**signature** count()

**returns** number

Counts the number of objects matching the query this does take limit/skip into consideration.

**example**
    
    
    var count = collection.find( query ).count();

* * *

### sort

**signature** sort(JSON orderBy)

**returns** [SparkMongoCursor](../Mongo/SparkMongoCursor)

Sorts this cursor's elements. This method must be called before getting any object from the cursor.

**example**
    
    
    var obj = collection.find( query ).sort( {"field" : 1} ).limit( 100 ).toArray();

* * *

### hasNext

**signature** hasNext()

**returns** boolean

Checks if there is another object available.

**example**
    
    
    var cursor = collection.find( query ); if( cursor.hasNext() ) {var obj = cursor.next();}

* * *

### next

**signature** next()

**returns** JSON

Returns the object the cursor is at and moves the cursor ahead by one.

**returns**

a JSON object

**example**
    
    
    var cursor = collection.find( query ); if( cursor.hasNext() ) {var obj = cursor.next();}

* * *

### curr

**signature** curr()

**returns** JSON

Returns the element the cursor is at.

**returns**

a JSON object

**example**
    
    
    var cursor = collection.find( query ); if( cursor.hasNext() ) {cursor.next(); var obj = cursor.curr();}