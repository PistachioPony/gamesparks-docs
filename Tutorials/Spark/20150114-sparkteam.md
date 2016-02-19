title: SparkTeam
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkteam
author: GameSparks
description: 
post_id: 5796
created: 2015/01/14 12:23:48
created_gmt: 2015/01/14 12:23:48
comment_status: open
post_name: sparkteam
status: publish
post_type: post

<!--Provides access to an instance of a team -->

# SparkTeam

[toc] 

Provides access to an instance of a team

e.g.
    
    
    var team = Spark.getTeams().getTeam(myTeamId);

* * *

### getOwnerId

**signature** getOwnerId()

**returns** string

Gets the playerId of the player who owns this team.

**example**
    
    
    var ownerId = Spark.getTeams().getTeam(myTeamId).getOwnerId();

* * *

### getTeamId

**signature** getTeamId()

**returns** string

Gets the teamId of this team.

**example**
    
    
    var teamId = Spark.getTeams().getTeam(myTeamId).getTeamId();

* * *

### getTeamType

**signature** getTeamType()

**returns** string

Gets the teamType of this team.

**example**
    
    
    var teamType = Spark.getTeams().getTeam(myTeamId).getTeamType();

* * *

### getMemberIds

**signature** getMemberIds()

**returns** string[]

Gets an array containing the playerIds of the members of this team.

**example**
    
    
    var memberIds = Spark.getTeams().getTeam(myTeamId).getMemberIds();

* * *

### setOwnerId

**signature** setOwnerId(string playerId)

**returns** boolean

Updates the ownerId of this team.

Returns true if the ownerId was successfully updated, otherwise false.

**example**
    
    
    var success = Spark.getTeams().getTeam(myTeamId).setOwnerId(newOwnerId);

* * *

### addMembers

**signature** addMembers(string[] playerIds)

**returns** void

Adds the given playerIds as members to this team.

**example**
    
    
    Spark.getTeams().getTeam(myTeamId).addMembers(myPlayerId1, myPlayerId2);

* * *

### removeMembers

**signature** removeMembers(string[] playerIds)

**returns** void

Removes the given playerIds from the list of members of this team.

**example**
    
    
    Spark.getTeams().getTeam(myTeamId).removeMembers(myPlayerId1, myPlayerId2);

* * *

### drop

**signature** drop()

**returns** boolean

Drops this team instance, deleting the underlying team data.

Returns true if the team has been dropped.

**example**
    
    
    var success = Spark.getTeams().getTeam(myTeamId).drop();

* * *

### listChatMessages

**signature** listChatMessages(number count, number offset)

**returns** [ChatMessage](../Helper/ChatMessage)[]

Lists the last 
    
    
    count

chat messages for this team, starting from the 
    
    
    offset

th message, most recent first.

**example**
    
    
    var history = Spark.getTeams().getTeam(myTeamId).listChatMessages(50, 0);

* * *

### getChatMessage

**signature** getChatMessage(string chatMessageId)

**returns** JSON

Get a message from the chat history by its id.

**example**
    
    
    var message = Spark.getTeams().getTeam(myTeamId).getChatMessage(chatMessageId);

* * *

### deleteChatMessage

**signature** deleteChatMessage(string chatMessageId)

**returns** boolean

Delete a message from the chat history by its id.

Returns true if the message has been removed from the chat history.

**example**
    
    
    var success = Spark.getTeams().getTeam(myTeamId).deleteChatMessage(chatMessageId);