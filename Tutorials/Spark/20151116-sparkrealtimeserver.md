title: SparkRealtimeServer
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkrealtimeserver
author: GameSparks
description: 
post_id: 9655
created: 2015/11/16 15:09:09
created_gmt: 2015/11/16 15:09:09
comment_status: closed
post_name: sparkrealtimeserver
status: publish
post_type: post

<!--Provides the details of the realtime server on which a match will be played out -->

# SparkRealtimeServer

[toc] 

Provides the details of the realtime server on which a match will be played out

e.g.
    
    
    var server = Spark.getMultiplayer().loadMatch(matchId).getServer();

* * *

### getHost

**signature** getHost()

**returns** string

**validity** All Scripts

**returns**

The hostname of the server

**example**
    
    
    var host = server.getHost()

* * *

### getPort

**signature** getPort()

**returns** number

**validity** All Scripts

**returns**

The port to connect to on the server

**example**
    
    
    var port = server.getPort()