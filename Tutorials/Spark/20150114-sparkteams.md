title: SparkTeams
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkteams
author: GameSparks
description: 
post_id: 5797
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: sparkteams
status: publish
post_type: post

<!--Provides access to teams for the current game. -->

# SparkTeams

[toc] 

Provides access to teams for the current game.

e.g.
    
    
    var team = Spark.getTeams().getTeam(myTeamId);

* * *

### getTeam

**signature** getTeam(string teamId)

**returns** [SparkTeam](../Spark/SparkTeam)

Returns a SparkTeam object that represents the team with the given teamId.

**example**
    
    
    var team = Spark.getTeams().getTeam(myTeamId);

* * *

### getTeamByOwnerIdAndTeamType

**signature** getTeamByOwnerIdAndTeamType(string ownerId, string teamType)

**returns** [SparkTeam](../Spark/SparkTeam)[]

Returns an array of SparkTeam objects for the given ownerId and teamType.

**example**
    
    
    var teams = Spark.getTeams().getTeamByOwnerIdAndTeamType(myOwnerId, myTeamType);