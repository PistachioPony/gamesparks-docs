---
nav_sort: 5
src: /Documentation/NoSQL Explorer.md

---

# NoSQL Explorer

From the NoSQL tab you have the ability to interact with the data stored on the platform.

![](img/1.png)

You can select the database you wish to look at from the drop-down in the top left of the page (as highlighed above). For any given game there will be a PREVIEW listing in this list, along with an optional LIVE listing if your game is in the published state.

## Collection Drop Down Menu Filtering

Each *Actions* tab has a drop down menu containing the list of collections that are available in your database. The collection filter switches allow you to turn sections of the drop-down menu on and off to make the list more manageable.

![](img/2.png)

The collection drop-down can also be filtered manually be typing the name of the collection you are looking for in the field. The results are dynamically updated as you type.

![](img/3.png)

## Actions

Once you have selected the correct DB you can choose from the following options in the Action section as highlighted above: *Find*, *Insert*, *Update*, *Remove*, *Aggregate*, *Create*, *Drop* and *Stats*.

### Find

[MongoDB Find Manual](http://docs.mongodb.org/manual/reference/method/db.collection.find)

From the *Find* tab you can execute queries against collections. For those of you with existing mongo experience, the find form builds a db.<collection>.find(<query>, <fields>).sort(<sort>).limit(<limit>).skip(<skip>) command based on the data populated in the form fields.

* *Collection* : Select the collection you want to query.
* *Query* : The query you want to execute in JSON form:
  * To find players with displayName "testUser" the following JSON should be used {"displayName" : "testUser"}
* *Sort* : The JSON representation of the sort for the query:
  * To sort by userName in ascending order the following JSON should be used {"userName" : 1}
* *Fields*: Allows you to limit the fields that are returned in the results:
  * This is useful for collections with large document.
  * To limit the results to only contain the userName and displayName the following JSON should be used : {"userName" : 1, "displayName" : 1}. 1 indicates inclusion and 0 indicates exclusion for a field. You cannot mix inclusion and exclusion in a single query.
* *Skip / Limit* : The number of documents to skip, useful for paging in combination with limit:
  * To get the 3rd page of 10 documents per page, use skip=20 and limit=10.
  * The maximum that the limit value can be set to for finds is 1000.

The *Find* tab allows you to export the results to a local file. Set up your query as normal and press the *Export* button. The maximum that the limit value can be set to for exports is 10000.

### Insert

[MongoDB Insert Manual](http://docs.mongodb.org/manual/reference/method/db.collection.insert)

You can insert documents directly into a collection from the Insert tab. Add the document you want to insert into the Document field.

* If the document you supply does not have an \_id field, mongo will create one for you.
* If the document you supply does have an \_id field and it is already in use within the collection the insert will fail.

### Update

[MongoDB Update Manual](http://docs.mongodb.org/manual/reference/method/db.collection.update)

From the Update tab you can modify an existing document(s) in a collection.

* *Query* : The selection criteria for the update. Use the same query selectors as used in the Find method.
* *Update* : The modifications to apply. 
* *Multi* : Set to true if all documents meeting the criteria should be modified.
* *Upsert* : Set to true to create a new document when no document matches the query.

### Remove

[MongoDB Remove Manual](http://docs.mongodb.org/manual/reference/method/db.collection.remove)

Removes all documents matching the supplied query from a collection.

* *Query* : The selection criteria for the Remove operate. All documents matching this criteria will be removed.

### Aggregate

[MongoDB Aggregate Manual](http://docs.mongodb.org/manual/reference/method/db.collection.aggregate)

Calculates aggregate values for data in the collection.

* *Pipeline* : A JSON array of pipeline commands. If you are supplying more than one pipeline stage you must wrap then within a JSON array.

### Create

Allows a new collection to be created. Collections can be created as runtime (non versioned) or metadata (versioned)

* *Name* : The name to give the collection. Metadata collections are prefixed with "meta.", and runtime collections are prefixed with "script." within the database.

### Drop

[MongoDB Drop Manual](http://docs.mongodb.org/manual/reference/command/drop)

Allows you to permanently remove a collection form the database.

### Stats

[MongoDB Stats Manual](http://docs.mongodb.org/manual/reference/method/db.collection.stats)

Returns statistics about the selected collection.
