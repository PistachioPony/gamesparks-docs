title: SparkRequest API
link: https://docs.gamesparks.net/documentation/cloud-code-api/sparkrequests-api
author: mantas.danilovas
description: 
post_id: 6218
created: 2015/03/19 14:11:53
created_gmt: 2015/03/19 14:11:53
comment_status: closed
post_name: sparkrequests-api
status: publish
post_type: post

# SparkRequest API

SparkRequest API allows you to send GameSparks Requests from within Cloud Code. Cloud code bound to these requests and responses are not executed when sent using this API. If you want to execute cloud code on the requests and responses you can do this by modularising your code and executing the same module before sending the request and after receiving the response. This restriction is in place to protect from infinite loops that could occur. You can see how this works [here](/?p=764). 

### Creating a Request

The Request object can be easily created using the following notation: 
    
    
    var authenticationRequest = new SparkRequests.AuthenticationRequest();

### Setting Request parameters

All of the parameters that are available for the particular Request, can be set using the following notation: 
    
    
    authenticationRequest.userName = "username";
    authenticationRequest.password = "password";

###  Sending the Request and grabbing the Response

There are a few ways to dispatch the request and they primarily differ by who the request is sent by: 
    
    
    // Send the request as currently Authenticated player and save the response JSON
    var authenticationResponse = Spark.sendRequest(authenticationRequest);
    // OR
    var authenticationResponse = authenticationRequest.Send();
    
    // Send the request as the player who's Id was provided and save the response JSON
    var authenticationResponse = Spark.sendRequestAs(authenticationRequest, playerId);
    // OR
    var authenticationResponse = authenticationRequest.SendAs(playerId);
    

###  The Response data

The Response is a JSON object that can be easily queried, here's an example: 
    
    
    var authenticationResponse = Spark.sendRequest(authenticationRequest);
    
    if(authenticationResponse.error != null){
        // Do something
    }