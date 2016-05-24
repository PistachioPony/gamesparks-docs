# Searching for Specific Players and Teams

## Introduction

The platform allows you to search for specific Players and Teams in your game no matter how big or small your collection of data is using very easy to use tools. We'll cover the use of NoSQL Explorer, the management screen and acquiring specific entries from Cloud Code with examples.  

## NoSQL Explorer

This powerful tool allows you to search for anything within your game down to the specifics of a certain index. For example you can search for certain players who have exactly 530 ammunition in their inventory or users that share the same name, the possibilties are endless.We will use the NoSQL explorer to search for a specific player's display name. The display name we'll be looking for will be "Coder". In the explorer we'll select the Player collection to limit our search to Players only. In the query field we'll specify what exactly we'll be looking for in our case the displayName "Coder" in the format {displayName : "Coder"}. Once we submit the search (Using enter, or the 'Find' button) the players which have have 'Coder' as their display name will be retrieved and all their database is displayed including scriptData, privateData, externalIDs and external authentication and many more fields that you may or may not want to see. However when you search for a certain specific field you can also limit what fields come back from the player database using the format {fieldName: 1} to include those fields or {fieldName:0} to exclude fields. So for our purpose we're going to limit the search to return displayName and userName fields only. For more information about the SQL Explorer, click [here](/developer-portal/nosql).

![](/img/TeamsPlayersSearch/1.jpg)

By changing the collection to 'Team' you can now search for specific teams and view their members which allows you then to take the member's ID and search for those members. If you submit an empty search for your Teams you will retrieve a list of all your Teams, this will help you see the fields you can query. You can search for a specific member by ID to see in which team that player belongs to or which teams have earned a certain achievement.

![](/img/TeamsPlayersSearch/2.jpg)
   

### Player Management Screen

Every game you make in GameSparks comes with our native Player management screen ,which can be found in the Manage tab, which you can quickly query to retrieve the players you're looking for or display every single player you have in your game's database. Unlike the NoSQL Explorer you can view player's details through a graphical interface that you can customise yourself through our dynamic forms builder, for more info, click [here](/tutorials/dynamic-forms-tutorial). You can also create a Team management screen that functions the same way.   To ensure that you get exactly what you want you can use rules or group of rules to narrow your search.

![](/img/TeamsPlayersSearch/3.jpg)

![](/img/TeamsPlayersSearch/4.jpg)


## Through Cloud Code

You can also search for Teams and Players in the cloud code while your game executes the requests and responses. This powerful convenience allows your users to find each other using events you've set up through Cloud code. The following code shows how to use the NoSQL collections to find specific players or teams based on the data we pass in and then using the ID to find references to those players or teams to access the rest of the data.

```    
    //Player search
    //Getting a player based on Query
    var players = Spark.systemCollection("player");

    var playerData = players.findOne({"displayName" : "Coder"}, {_id : 1, displayName:1}); //Find the display name 'Coder' and return the players that have it.

    //Or you can have the player ID saved
    var playerID = "5602c3dce4b07961f34b68c3" //Manually set the ID

    //Finding the player through their ID
    var playerVar = Spark.loadPlayer(playerData.$oid); //or (playerID) //Make a reference for that player through their ID.


    //Team search
    //Getting a Team based on Query
    var Teams = Spark.systemCollection("teams");

    var teamData = Teams.findOne({"teamName" : "BlueGang"}, {_id : 1, teamName:1}); //Find the team name 'BlueGang' and return the teams that have it

    //Or you can have the player ID saved
    var teamID = "GameSparks Team" //manually set the ID

    //Finding the player through their ID
    var teamVar = Spark.getTeams().getTeam(teamData.$oid); // or (teamID) //Make a reference for that team through the ID

```
