title: SparkLeaderboardEntry
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkleaderboardentry
author: GameSparks
description: 
post_id: 4581
created: 2014/08/14 10:26:33
created_gmt: 2014/08/14 10:26:33
comment_status: closed
post_name: sparkleaderboardentry
status: publish
post_type: post

<!--An entry within a leaderboard. -->

# SparkLeaderboardEntry

[toc] 

An entry within a leaderboard.

e.g.
    
    
    var entry = leaderboard.getEntries().next();

* * *

### getUserId

**signature** getUserId()

**returns** string

Returns the playerId of the player whose entry in the leaderboard this is.

**example**
    
    
    var playerId = entry.getUserId();

* * *

### getUserName

**signature** getUserName()

**returns** string

Returns the displayName of the player whose entry in the leaderboard this is.

**example**
    
    
    var displayName = entry.getUserName();

* * *

### getRank

**signature** getRank()

**returns** number

Returns the position of this entry within the leaderboard.

**example**
    
    
    var rank = entry.getRank();

* * *

### getRankPercentage

**signature** getRankPercentage()

**returns** number

Returns the rank of the player as a percentage of total entries.

**example**
    
    
    var rankPercentage = entry.getRankPercentage();

* * *

### getWhen

**signature** getWhen()

**returns** string

Returns a String representing the time this entry was recorded, in the format yyyy-MM-dd'T'HH:mm'Z'.

**example**
    
    
    var when = entry.getWhen();

* * *

### getAttribute

**signature** getAttribute(string name)

**returns** JSON

Returns the attribute **name** from this leaderboard entry. Use this to get custom attributes from this entry.

**params**

name - the name of the attribute to be returned

**example**
    
    
    var score = entry.getAttribute("SCORE");