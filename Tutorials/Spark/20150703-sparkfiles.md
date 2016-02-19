title: SparkFiles
link: https://docs.gamesparks.net/documentation/cloud-code-api/utils-cloud-code-api/sparkfiles
author: GameSparks
description: 
post_id: 8261
created: 2015/07/03 16:52:40
created_gmt: 2015/07/03 16:52:40
comment_status: closed
post_name: sparkfiles
status: publish
post_type: post

<!--Provides access uploaded files along with downloadables -->

# SparkFiles

[toc] 

Provides access uploaded files along with downloadables

* * *

### deleteUploadedFile

**signature** deleteUploadedFile(string uploadId)

**returns** boolean

**validity** All Scripts

Deletes a previously uploaded file by uploadId

**params**

uploadId - the id of the uploaded file

**example**
    
    
    Spark.getFiles().deleteUploadedFile("myUploadId");

* * *

### uploadedXml

**signature** uploadedXml(string uploadId)

**returns** [SparkXmlReader](../Utils/SparkXmlReader)

**validity** All Scripts

Provides access to an uploaded file via a SparkXmlReader interface

**params**

uploadId - the id of the uploaded file

**example**
    
    
    var reader = Spark.getFiles().uploadedXml("myUploadId");

* * *

### uploadedJson

**signature** uploadedJson(string uploadId)

**returns** JSON

**validity** All Scripts

Provides access to an uploaded file via a JSON object

**params**

uploadId - the id of the uploaded file

**returns**

A JSON object

**example**
    
    
    var reader = Spark.getFiles().uploadedJson("myUploadId");

* * *

### downloadableXml

**signature** downloadableXml(string shortCode)

**returns** [SparkXmlReader](../Utils/SparkXmlReader)

**validity** All Scripts

Provides access to a downloadable file via a SparkXmlReader interface

**params**

shortCode - the short code for the downloadable file

**returns**

**example**
    
    
    var reader = Spark.getFiles().downloadableXml("shortCode");

* * *

### downloadableJson

**signature** downloadableJson(string shortCode)

**returns** JSON

**validity** All Scripts

Provides access to a downloadable file via a JSON object

**params**

shortCode - the short code for the downloadable file

**returns**

**example**
    
    
    var reader = Spark.getFiles().downloadableJson("shortCode");