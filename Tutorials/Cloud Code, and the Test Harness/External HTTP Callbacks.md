---
src: Tutorials/Cloud Code, and the Test Harness/External HTTP Callbacks.md
---

# How to implement external HTTP Callbacks

You have the ability to get external servers (or your own processes) to make HTTP calls into the GameSparks platform, and when these calls are made you can execute some custom cloud code to do whatever processing you need. The HTTP request can either be a GET or POST request, and all parameters passed to the server are accessible via the Spark.getData() function. It should be noted that if you pass query string parameters on a POST request both sets of values are accessible. Single parameters are passed to javascript as Strings, and in the case of multiple parameters with the same name, these values are passed to JavaScript as a String array. POST parameters are only interpreted into the data object when the content type of the request is "multipart/form-data", for other usages see the section "Reading POST Data" at the bottom of this article

## Creating Cloud Code to handle the request

To create a script to handle the request, from the cloud code page, select the "System" submenu and use the "Callback URL" menu entry.

## The callback URL

https://{stage}.gamesparks.net/callback/{apiKey}/{serverSecret}/{playerId}

  * *stage* : "preview" or "service" (depending on whether you are accessing the live servers or not)
  * *apiKey* : The API Key of you game
  * *serverSecret* : The server secret of you game, accessible from the game overview page by clicking the __ icon
  * *playerId(optional)* : The ID of the player, it this is supplied then Spark.getPlayer()  will be the player specified

## Adding parameters

For  GET request, additional parameters can be added to the query string that are passed to your script. For example https://{stage}.gamesparks.net/callback/{apiKey}/{serverSecret}/{playerId}?attr1=abc&attr2=bcd&attr2=cde With this url the following code can be used to access these parameters

``{}    
    //attribute1 is a string
    var attribute1 = Spark.getData().attr1;

    //attribute2 is an array
    var attribute2 = Spark.getData().attr2;

    //attribute2[0] is bcd
    //attribute2[1] is cde
``

## Producing output

The scriptData object from the callback script is written to the output stream as a JSON document.

``{}    
    Spark.setScriptData("key1", "value1");
    Spark.setScriptData("key2", "value2");
``
Will generate the JSON output

``{}    
    {
        "key1": "value1",
        "key2": "value2"
    }
``

  If you do not want to write JSON but your own text based output, setting a value with the key "RESPONSE_RAW" in script data will override the JSON output and return this value directly.

``{}    
    Spark.setScriptData("RESPONSE_RAW", "OK");
``

Will generate the response as :


    OK

## Reading POST data

There are instances where a remote server may not set the content-type header correctly, and the post data is not automatically translated into Spark.getData(). In these cases, the POST requests have an additional attribute set into Spark.getData() of "REQUEST_BODY". This is the body of the HTTP post request as a string, so you can do your own parsing of this value.

``{}    
    var rawPostData = Spark.getData().REQUEST_BODY
    ``
