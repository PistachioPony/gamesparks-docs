title: SparkLeaderboardCursor
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkleaderboardcursor
author: GameSparks
description: 
post_id: 4580
created: 2014/08/14 10:26:31
created_gmt: 2014/08/14 10:26:31
comment_status: closed
post_name: sparkleaderboardcursor
status: publish
post_type: post

<!--A cursor over entries within a leaderboard. -->

# SparkLeaderboardCursor

[toc] 

A cursor over entries within a leaderboard.

e.g.
    
    
    var leaderboard = Spark.getLeaderboards().getLeaderboard(shortCode).getEntries();

* * *

### hasNext

**signature** hasNext()

**returns** boolean

Returns true if there are more entries available.

**example**
    
    
    var hasNext = cursor.hasNext();

* * *

### next

**signature** next()

**returns** [SparkLeaderboardEntry](../Spark/SparkLeaderboardEntry)

Returns the entry the cursor is at and moves the cursor ahead by one.

**example**
    
    
    var entry = cursor.next();