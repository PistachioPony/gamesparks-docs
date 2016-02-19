title: SparkHttp
link: https://docs.gamesparks.net/documentation/cloud-code-api/comms-cloud-code-api/sparkhttp
author: gabriel.page
description: 
post_id: 2391
created: 2014/05/08 11:07:16
created_gmt: 2014/05/08 11:07:16
comment_status: closed
post_name: sparkhttp
status: publish
post_type: post

<!--Provides access to a HTTP client object. -->

# SparkHttp

[toc] 

Provides access to a HTTP client object.

e.g.
    
    
    var httpSender = Spark.getHttp("http://somehost");

* * *

### setBasicAuth

**signature** setBasicAuth(string username, string password)

**returns** [SparkHttp](../Comms/SparkHttp)

Sets credentials to be used for Basic Auth

**params**

userName - the username to use

password - the password to use

**example**
    
    
    Spark.getHttp(url).setBasicAuth("myusername", "mypassword");

* * *

### setHeaders

**signature** setHeaders(JSON headers)

**returns** [SparkHttp](../Comms/SparkHttp)

Add custom header to the request

**params**

headers - A JSON object

**example**
    
    
    Spark.getHttp(url).setHeaders({"X-Custom-header":"1234"});

* * *

### get

**signature** get()

**returns** [SparkHttpResponse](../Comms/SparkHttpResponse)

Perform a HTTP GET request

**example**
    
    
    var response = Spark.getHttp(url).get();

* * *

### postForm

**signature** postForm(JSON form)

**returns** [SparkHttpResponse](../Comms/SparkHttpResponse)

Perform a HTTP POST using a JSON form object

**params**

form - the HTTP form data

**example**
    
    
    Spark.getHttp(url).postForm(form);

* * *

### postXml

**signature** postXml(XMLObject form)

**returns** [SparkHttpResponse](../Comms/SparkHttpResponse)

Perform a HTTP POST using an XML form object

**params**

form - the HTTP form data

**example**
    
    
    Spark.getHttp(url).postXml(xmlForm);

* * *

### postJson

**signature** postJson(JSON form)

**returns** [SparkHttpResponse](../Comms/SparkHttpResponse)

Perform a HTTP POST using a JSON form object

**params**

form - the HTTP form data

**example**
    
    
    Spark.getHttp(url).postJson(jsonForm);

* * *

### postString

**signature** postString(string data)

**returns** [SparkHttpResponse](../Comms/SparkHttpResponse)

Perform a HTTP POST using a string

**params**

data - the HTTP POST data

**example**
    
    
    Spark.getHttp(url).postString(data);