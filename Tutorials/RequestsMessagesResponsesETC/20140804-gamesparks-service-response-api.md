title: GameSparks Service - Response API
link: https://docs.gamesparks.net/documentation/response-api/gamesparks-service-response-api
author: GameSparks
description: 
post_id: 4356
created: 2014/08/04 15:33:05
created_gmt: 2014/08/04 15:33:05
comment_status: closed
post_name: gamesparks-service-response-api
status: publish
post_type: post

# GameSparks Service - Response API

[su_tabs] [su_tab title="Common"] A number of common parameters are available on Request and Response objects. 

## Common Request Parameters

Name Required Description

requestId
TRUE
The SDK adds a requestId to all requests, this is used to match responses from the websocket.

## Common Response Attributes

Name Type Description

error
JSON
A JSON Map of an errors that were encountered while processing the request

scriptData
JSON
A JSON Map of any data added either to the Request or the Response by your Cloud Code

requestId
String
The ID of the corresponding Request
[/su_tab] [su_tab title="Authentication"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="authentication-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Store"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="store-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Player"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="player-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Challenges"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="challenges-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Leaderboards"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="leaderboards-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Analytics"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="analytics-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"] [/su_tab] [su_tab title="Misc"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="misc-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"][/su_tab] [su_tab title="Teams"] [su_posts template="templates/simple-loop.php" post_type="post" taxonomy="category" tax_term="teams-response-api" order="asc" orderby="title" post_status="any" posts_per_page="-1"][/su_tab] [/su_tabs]