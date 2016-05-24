# How to create a team Leaderboard

Using the GameSparks platform, you can create Leaderboards that show the performance of a team, rather than the performance of a single players. For team-based Leaderboards, you need a few things in place. This post will take you through the process of getting them set up. In this example we'll create a team type called "Squad". When a player posts a score, the team they are in will be attributed with the score, and this can then be used on a Leaderboard for the team.

## Creating a Team Type

From the Teams menu in the Configurator, click the add icon to create your team type.

![](img/TeamLDR/1.jpg)

We've set the team to have a Maximum Members number of 5.

## Creating the event

We'll create a simple high score event that takes a single score parameter.

![](img/TeamLDR/2.jpg)

In this example, the score we are passing should be added to all the previous scores submitted towards that team. So we've set the "_Default Calc_" to sum them up. This will create the default Running Total for the event, allowing us to track the score for a player.

## Creating the Team Running Total

We also want to track the score for the team. We'll need to create another Running Total for the high score event, that tracks the value for a team rather than for a player.

![](img/TeamLDR/3.jpg)

The key change in this running total is that we have set the "_Type_" parameter to the team type we want this running total to track. We are now in a position where the GameSparks platform is going to track a running total for each Squad, and will sum together each score submitted by each member.

## Creating the Leaderboard

We create the leaderboard in the same we we would for personal leaderboards, but we'll specify the team type the leaderboard is for in the "_Type_" parameter.

![](img/TeamLDR/4.jpg)

## Team Notifications

Notifications are processed slightly differently for team personal leaderboards and based leaderboards. The differences are detailed in the table below: [su_table]

Notification Personal Leaderboard Team Leaderboard

New High Score
When a player posts a new high score to this leaderboard, they will receive a NewHighScoreMessage
When a player posts a new high score to this leaderboard, they will receive a NewTeamScoreMessage

Social Notifications
 When a player beats his friends, they will receive a SocialRankChangedMessage
When a player posts new high score to this leaderboard, the other team members will receive a NewTeamScoreMessage

Top N Notifications
 When a player's rank is increased due to a new score being posted (and they are in the top N of the leaderboard) they will receive a GlobalRankChangedmessage
When a teams rank is increased due to a new score being posted (and they are in the top N of the leaderboard) they will receive a TeamRankChangedmessage
[/su_table]

## Testing the configuration

### Create the first player

Request

```
    {
     "@class": ".RegistrationRequest",
     "userName": "Testing1",
     "password": "password",
     "displayName": "Test User 1",
     "requestId": "1403266652739"
    }
```
Response

```
    {
     "@class": ".RegistrationResponse",
     "authToken": "406da13f-a124-43cb-ac96-b545aab0245a",
     "displayName": "Test User 1",
     "requestId": "1403266652739",
     "scriptData": null,
     "userId": "53a426ea79b42ce7ea4c4570"
    }
```
### Create a Squad

We'll use the CreateTeamRequest API to create a SQUAD that'Yorks owned by the current player. Request

```
    {
     "@class": ".CreateTeamRequest",
     "teamId": "53a426ef79b42ce7ea4c4576",
     "teamName": "First Test Squad",
     "teamType": "SQUAD",
     "requestId": "1403266702171" }
```
Response The response contains the team details, notice the current player is automatically added as a member.

```
    {
     "@class": ".CreateTeamResponse",
     "requestId": "1403266702171",
     "scriptData": null,
     "owner": {
      "id": "53a426ea79b42ce7ea4c4570",
      "displayName": "Test User 1",
      "online": true
     },
     "teamId": "53a426ef79b42ce7ea4c4576",
     "teamType": "SQUAD",
     "members": [
      {
       "id": "53a426ea79b42ce7ea4c4570",
       "displayName": "Test User 1",
       "online": true
      }
     ]
    }
```
### Create the second Player

Request

```
    {
     "@class": ".RegistrationRequest",
     "userName": "Testing2",
     "password": "password",
     "displayName": "Test User 2",
     "requestId": "1403266652739"
    }
```
Response

```
    {
     "@class": ".RegistrationResponse",
     "authToken": "23ec1f1a-ca15-4a2c-b7fa-3d2d28cfd643",
     "displayName": "Test User 2",
     "requestId": "1403266652739",
     "scriptData": null,
     "userId": "53a4274479b42ce7ea4c459b"
    }
```
### Join the Squad

Request To join the squad, we'll pass in the teamId of the previously created team

```
    {
     "@class": ".JoinTeamRequest",
     "teamId": "53a426ef79b42ce7ea4c4576",
     "requestId": "1403266924118"
    }
```
Response The response contains the new team details, you'll see that the current player has now been added to the team as a member.

```
    {
     "@class": ".JoinTeamResponse",
     "requestId": "1403266924118",
     "scriptData": null,
     "owner": {
      "id": "53a426ea79b42ce7ea4c4570",
      "displayName": "Test User 1",
      "online": false
     },
     "teamId": "53a426ef79b42ce7ea4c4576",
     "teamType": "SQUAD",
     "members": [
      {
       "id": "53a426ea79b42ce7ea4c4570",
       "displayName": "Test User 1",
       "online": false
      },
      {
       "id": "53a4274479b42ce7ea4c459b",
       "displayName": "Test User 2",
       "online": true
      }
     ]
    }
```
### Post a Score as Player 2

Request We post a score of 10 into the platform.

```
    {
     "@class": ".LogEventRequest",
     "eventKey": "HS",
     "SCORE": "10",
     "requestId": "1403267110914"
    }
```
Response

```
    {
     "@class": ".LogEventRequest",
     "eventKey": "HS",
     "SCORE": "10",
     "requestId": "1403267110914"
    }
```
Message As we know this is the first score posted for this team we receive a NewHighScore message showing that the Squad we've created has a new high score of 10.

```
    {
     "@class": ".NewTeamScoreMessage",
     "messageId": "53a4286d79b465bde20a475c",
     "notification": true,
     "summary": ".NewTeamScoreMessage",
     "leaderboardData": {
      "teamId": "53a426ef79b42ce7ea4c4576",
      "SUM-SCORE": 10,
      "teamName": "First Test Squad",
      "when": "2014-06-20T12:26Z"
     },
     "rankDetails": {
      "globalTo": 1
     },
     "achievementsEarned": [
      "GT1"
     ],
     "leaderboardName": "Team LB",
     "leaderboardShortCode": "SQUAD_LB"
    }
```
### Authenticate as player 1

Request

```
    {
     "@class": ".AuthenticationRequest",
     "userName": "Testing1",
     "password": "password",
     "requestId": "1403267256818"
    }
```
Response

```
    {
     "@class": ".AuthenticationResponse",
     "authToken": "baaeef21-d4f3-4354-83ad-3fb39097e0bb",
     "displayName": "Test User 1",
     "requestId": "1403267256818",
     "scriptData": null,
     "userId": "53a426ea79b42ce7ea4c4570"
    }
```
### Post a Score as Player 1

Request This time we'll post a score of 15.

```
    {
     "@class": ".LogEventRequest",
     "eventKey": "HS",
     "SCORE": 15,
     "requestId": "1403267448095"
    }
```

Response

```
{
 "@class": ".LogEventResponse",
 "requestId": "1403267448095",
 "scriptData": null
}
```
Message We receive a new TeamScoreMessage, showing that the teams score is now 25 (10 + 15)

```
{
 "@class": ".NewTeamScoreMessage",
 "messageId": "53a42a3379b466eb3efde616",
 "notification": true,
 "summary": ".NewTeamScoreMessage",
 "leaderboardData": {
  "teamId": "53a426ef79b42ce7ea4c4576",
  "SUM-SCORE": 25,
  "teamName": "First Test Squad",
  "when": "2014-06-20T12:33Z"
 },
 "rankDetails": {
  "globalFrom": 1,
  "globalTo": 1
 },
 "leaderboardShortCode": "SQUAD_LB",
 "leaderboardName": "Team LB"
}
```
