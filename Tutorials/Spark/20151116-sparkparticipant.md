title: SparkParticipant
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkparticipant
author: GameSparks
description: 
post_id: 9653
created: 2015/11/16 15:08:14
created_gmt: 2015/11/16 15:08:14
comment_status: closed
post_name: sparkparticipant
status: publish
post_type: post

<!--Provides the details of a participant in a match -->

# SparkParticipant

[toc] 

Provides the details of a participant in a match

e.g.
    
    
    var participant = Spark.getMultiplayer().loadMatch(matchId).getParticipants[0];

* * *

### getPlayer

**signature** getPlayer()

**returns** [SparkPlayer](../Spark/SparkPlayer)

**validity** All Scripts

**returns**

The SparkPlayer this participant represents

**example**
    
    
    var player = participant.getPlayer()

* * *

### getPeerId

**signature** getPeerId()

**returns** number

**validity** All Scripts

**returns**

The peerId of this participant

**example**
    
    
    var peerId = participant.getPeerId()

* * *

### getAccessToken

**signature** getAccessToken()

**returns** string

**validity** All Scripts

**returns**

An accessToken for this participant to connect to the realtime server

**example**
    
    
    var accessToken = participant.getAccessToken()