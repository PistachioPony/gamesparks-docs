# SparkTeam

Provides access to an instance of a team

e.g.

<pre rel="highlighter" code-brush="js" contenteditable="false">var team = Spark.getTeams().getTeam(myTeamId);</pre>


## getOwnerId
_signature_ getOwnerId()</p>
_returns_ string</p>
Gets the playerId of the player who owns this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var ownerId = Spark.getTeams().getTeam(myTeamId).getOwnerId();</pre>

## getTeamId
_signature_ getTeamId()</p>
_returns_ string</p>
Gets the teamId of this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var teamId = Spark.getTeams().getTeam(myTeamId).getTeamId();</pre>

## getTeamType
_signature_ getTeamType()</p>
_returns_ string</p>
Gets the teamType of this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var teamType = Spark.getTeams().getTeam(myTeamId).getTeamType();</pre>

## getMemberIds
_signature_ getMemberIds()</p>
_returns_ string[]</p>
Gets an array containing the playerIds of the members of this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var memberIds = Spark.getTeams().getTeam(myTeamId).getMemberIds();</pre>

## setOwnerId
_signature_ setOwnerId(string playerId)</p>
_returns_ boolean</p>
Updates the ownerId of this team.
Returns true if the ownerId was successfully updated, otherwise false.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var success = Spark.getTeams().getTeam(myTeamId).setOwnerId(newOwnerId);</pre>

## addMembers
_signature_ addMembers(string[] playerIds)</p>
_returns_ void</p>
Adds the given playerIds as members to this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getTeams().getTeam(myTeamId).addMembers(myPlayerId1, myPlayerId2);</pre>

## removeMembers
_signature_ removeMembers(string[] playerIds)</p>
_returns_ void</p>
Removes the given playerIds from the list of members of this team.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getTeams().getTeam(myTeamId).removeMembers(myPlayerId1, myPlayerId2);</pre>

## drop
_signature_ drop()</p>
_returns_ boolean</p>
Drops this team instance, deleting the underlying team data.
Returns true if the team has been dropped.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var success = Spark.getTeams().getTeam(myTeamId).drop();</pre>

## listChatMessages
_signature_ listChatMessages(number count, number offset)</p>
_returns_ [ChatMessage](../Helper/ChatMessage.md)[]</p>
Lists the last <pre>count</pre> chat messages for this team, starting from the <pre>offset</pre>th message, most recent first.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var history = Spark.getTeams().getTeam(myTeamId).listChatMessages(50, 0);</pre>

## getChatMessage
_signature_ getChatMessage(string chatMessageId)</p>
_returns_ JSON</p>
Get a message from the chat history by its id.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var message = Spark.getTeams().getTeam(myTeamId).getChatMessage(chatMessageId);</pre>

## deleteChatMessage
_signature_ deleteChatMessage(string chatMessageId)</p>
_returns_ boolean</p>
Delete a message from the chat history by its id.
Returns true if the message has been removed from the chat history.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var success = Spark.getTeams().getTeam(myTeamId).deleteChatMessage(chatMessageId);</pre>

