title: Creating tournaments (using Teams and Multiplayer)
link: https://docs.gamesparks.net/?p=10653
author: omar.albadry
description: 
post_id: 10653
created: 2016/02/08 19:59:38
created_gmt: 
comment_status: closed
post_name: 
status: draft
post_type: post

# Creating tournaments (using Teams and Multiplayer)

## Introduction

Creating a tournament is a complex task that requires a lot of data management to determine who's on top, at what level the teams are competing at and how teams are matched. Especially when teams are competing and individual players' records are being tracked. GameSparks simplifies the creation of tournaments by offering out of the box components that when combined can be used to create complex functionality which can either be automated or triggered by certain players or server. This tutorial will show one of the ways in which you can create a team tournament.  

## The setup

### Tournament Collection

To create a collection, please refer to this [tutorial](/developer-portal/nosql). This collection will keep track of teams, how many games they've won and at what stage they are at. The collection will also have a name, which makes it easy to get hold of and use in matchmaking and leaderboards. The two fields for the collection will be: 

  * Teams, which will be an array which contains a JSON for every element that belongs to a team. This will make it easy to loop through and track teams.
  * Number, the number of the tournament for reference.
  How a simple tournament collection will look like eventually, with data in it:
    
    
    {
     "_id": {
      "$oid": "56b3716ce4b099193b9e6844"
     },
     "Data": {
      "teams": [
       {
        "TeamID12345": {
         "AmountOfTimesWon": 3,
         "stage": 2
        }
       },
       {
        "RedTeam": {
         "AmountOfTimesWon": 1,
         "stage": 1
        }
       }
      ],
      "tournamentNumber": 1
     }
    }

 

### Tournament Leaderboard

For the creation of our leaderboard we'll make an event first, the event attributes will be: 

  * Score, the score of our team which will have a default calc of sum
  * Stage, which will be used to determine the current stage of the team
  * tournament, which will be used to partition the leaderboard
 
The leaderboard setup : ![](/wp-content/uploads/2016/02/bandicam-2016-02-08-19-30-36-155-300x157.jpg)
  Tournament Match 

GameSparks' matchmaking system comes ready with all that we need to ensure teams are matched up based on stage, tournament type and tournament the team belongs to. One member of the team initiates the match and the system takes care of the rest. This match will be setup from by an event through Cloud code instead of being traditionally called by a matchmaking request from the player.
Match setup: ![](/wp-content/uploads/2016/02/bandicam-2016-02-08-19-50-00-543-300x86.jpg)
   

### Tournament Match up Event

The event will have no attributes but will be triggered by any member of the team. This event will find the team the player belongs to and will search for it in our tournament collection. Once found the document the team belongs to will be returned and used for the match making. If no documents are found the Cloud code will search for a tournament which has enough space (determined by you) if there is space that team will be placed in the appropriate tournament. If no tournaments are found, then a new one is created and the team is placed in it.   The event's Cloud code:
    
    
    //Reference to player
    var tourniPlayer = Spark.getPlayer();
    
    //Instance of GetMyTeams request
    var request = new SparkRequests.GetMyTeamsRequest();
    
    //Pass in the values needed for the request
    request.teamTypes = "tourniTeam";
    
    //Send request
    var response = request.Send();
    
    //Reference the first team (Assuming that the player only one team of type 'tourniTeam')
    var teamVar = Spark.getTeams().getTeam(response.teams[0].teamId);
    
    //Load our tournaments collection
    var tourniCollection = Spark.runtimeCollection("teamTournaments");
    
    //Find our team's ID in the collection and reference the document that it belongs to
    var teamData = tourniCollection.findOne( {"Data.teams" : {$nin : [teamVar.teamId]}});
    
    
    
    //If no record exists, allocate a space for our team, if none exist, make a new document
    if(!teamData){
        //Run the newTeam module
        require("newTeam");
    }
    else{
        //If our record exists, loop through the teams array to find our team
        teamData.Data.teams.forEach(retrieveData);
    }
    
    
    function retrieveData(entry){
        
        //Reference the team name
        var teamName = Object.keys(entry)[0];
        
        //If the team name is the one we're looking for
        if(teamName === teamVar.teamId){
          
            //Instance of Matchmaking request
            var matchRequest = new SparkRequests.MatchmakingRequest();
           
            //We make sure that player's are only matched to players in the same tournament
            matchRequest.matchGroup = teamData.Data.tournamentNumber;
            //Make sure it's the correct match type
            matchRequest.matchShortCode = "tourniMatch";
            //Use skill to match players to the correct stage in the tournament
            matchRequest.skill = entry[teamName].stage;
            //Send request and reference response
            var matchResponse = matchRequest.Send();
            
            //If no error
            if(!matchResponse.error){
                //Return as scriptData
                var responseData = matchResponse.scriptData;
            }
            else{
            //Create error message
            Spark.setScriptError("Error", "Problem with finding match")
            }
          
          
        }
        
    }

To learn about modules, click [here](/developer-portal/cloud-code). The 'newTeam' module: 
    
    
    //Find how many tournaments we have
    var tournaments = Spark.runtimeCollection("teamTournaments").find();
    
    //Reference length
    var length = tournaments.count();
    var tournCount = 0;
    
    //Loop through documents
    if(tournaments.hasNext()){
        
        //Increment count for reference
        tournCount++;
        //Reference current document and prepare to check next one
        var documentVar = tournaments.next();
        
        //If the tournament(Current document) has less than N teams 
        if(documentVar.Data.teams.length < 4)
        {
            //Create our JSON with our dynamic key (TeamID)
            var dynamicJson = {};
            
            //Construct JSON with our keyID as our teamID + record and stage
            dynamicJson[teamVar.teamId] =  {"AmountOfTimesWon": 0,"stage": 1}
            //Update the document by pushing our new team into the teams array
            Spark.runtimeCollection("teamTournaments").update({"_id" : { "$oid" : documentVar._id.$oid }}, {$push : {"Data.teams": dynamicJson}});
            
        }
        
        //If no document has enough space, create a new one
        if(tournCount === length){
            
          createNew();
          //break;
        }
        
    }
    
    
    if(!tournaments.hasNext())
    {
       createNew();
    }
    
    
    function createNew(){
        //Create a new document with our template which contains a teams array and the tournament number
        if(Spark.runtimeCollection("teamTournaments").insert({ "Data" :  { "teams" : []  , "tournamentNumber" : length + 1}  })) {
        //Create our JSON with our dynamic key (TeamID)
            var dynamicJson = {};
            
        //Construct JSON with our keyID as our teamID + record and stage