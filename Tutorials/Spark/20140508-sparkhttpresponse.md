title: SparkHttpResponse
link: https://docs.gamesparks.net/documentation/cloud-code-api/comms-cloud-code-api/sparkhttpresponse
author: gabriel.page
description: 
post_id: 2392
created: 2014/05/08 11:10:20
created_gmt: 2014/05/08 11:10:20
comment_status: closed
post_name: sparkhttpresponse
status: publish
post_type: post

<!--Represents the response form the HTTP call. -->

# SparkHttpResponse

[toc] 

Represents the response form the HTTP call.

e.g.
    
    
    var headers = response.getHeaders();

* * *

### getHeaders

**signature** getHeaders()

**returns** JSON

Returns the headers from the response.

**returns**

A JSON object containing the headers

**example**
    
    
    var response = Spark.getHttp(url).get();
    
    
    var headers = response.getHeaders();

* * *

### getResponseCode

**signature** getResponseCode()

**returns** number

Returns the response code.

e.g. 200

**returns**

the HTTP status code

**example**
    
    
    var response = Spark.getHttp(url).get();
    
    
    var statusCode = response.getResponseCode();

* * *

### getResponseString

**signature** getResponseString()

**returns** string

Returns the body from the response.

**returns**

A string representing the body of the response.

**example**
    
    
    var response = Spark.getHttp(url).get();
    
    
    var body = response.getResponseString();

* * *

### getResponseXml

**signature** getResponseXml()

**returns** JSON

Returns the body from the response as XML.

**returns**

A JSON representing the body of the response.

**example**
    
    
    var response = Spark.getHttp(url).get();
    
    
    var body = response.getResponseXml();

* * *

### getResponseJson

**signature** getResponseJson()

**returns** JSON

Returns the body from the response as JSON.

**returns**

A string representing the body of the response.

**example**
    
    
    var response = Spark.getHttp(url).get();
    
    
    var body = response.getResponseJson();