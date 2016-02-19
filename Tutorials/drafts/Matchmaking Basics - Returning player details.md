## Match Making Basics- Retaining player details

## Introduction

Once you match players together you will have reference to other player's PlayerIDs and account variables to use in Cloud code and use of useful platform features. One of these features would be the easy access of player data. This will enable you to load player specific options, settings and personal data the moment the match is made.  

## Access player data

To access player data from a list of opponents in a match:

  * Call the MatchDetails request using the ID of the match which contains the players you wish to access.
  * Once you receive the response You can access the opponent array which contains player data object which allow easy access to Achievements, Virtual Goods, Display name, online status, ID and ScriptData for any custom data saved against the player.
 

  ```  
    {
     "@class": ".MatchDetailsResponse",
     "matchId": "565dc32ce4b0905d7600a5a0",
     "opponents": [
      {
       "achievements": [
        "Cloud_Achievement",
        "Fastest_First"
       ],
       "online": true,
       "id": "563b423ce4b0f85acff00a61",
       "displayName": "Dummy2"
      },
      {
       "achievements": [
        "Cloud_Achievement"
       ],
       "online": false,
       "id": "563b4243e4b0f85acff00a69",
       "displayName": "Dummy3"
      },
      {
       "achievements": [
        "Cloud_Achievement"
       ],
       "online": false,
       "id": "563b4249e4b0f85acff00a71",
       "displayName": "Dummy4"
      }
     ],
     "playerId": "563b4235e4b0f85acff00a22",
     "scriptData": null
    }
```

Notice the ScriptData isn't included in response JSON but it's still accessible. If ScriptData was included in the JSON the JSON would be huge.
