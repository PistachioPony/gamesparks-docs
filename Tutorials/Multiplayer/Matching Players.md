---
src: /Tutorials/Multiplayer/Matching Players.md
---

# How to Match Players

In this tutorial, you will create Match configuration with customised Thresholds in the GameSparks Portal and perform a Match in the Test Harness that will match Players in the game. As a brief example of these features, I may want to match Players based on their similar skill level in my game, so that Players can play against someone of equal ability to make it more enjoyable for all.  

## Creating a Match

*1.* To create a Match, navigate to the Portal's *Configurator *and go to the *Multiplayer* section.

*2.* In the *Multiplayer* section, select the *Matches* tab and click the *Add* button to create a new Match.

![](img/HowToMatchPlayers/1.png)  

*3.* In the *Create Match* form, specify the Short Code, Name and Description of your Match and select the *Add* button to create the desired number of thresholds you want in the Match.


![](img/HowToMatchPlayers/2.png)  

The *Create Form* contains the following fields:

* *Short Code* \- Identifier for the Match.
* *Name* \- Name for the Match.
* *Description* \- A descriptive explanation of what the Match is.
* *Min. Players* \- The minimum amount of Players for the Match to be legitimate.
* *Max. Players* \- The maximum amount of Players that can be on the Match.
 

## Head-to-Head Matching vs. Multiplayer Matching

The values set in the *Min. Players* and *Max. Players* fields, will determine whether you are creating a Head-to-Head Match or a Multiplayer Match for more than 2 Players. The value in *Min. Players* cannot be less than 2 players.

Multiplayer Matching is based on synchronous messages that match Players based on similar skill attributes, continuously adding Players to the Match and updating those already in the Match until the specified maximum number of Players has been reached, similar to the way a Challenge works.  

*4.* Set both the *Min. Players* and *Max. Players* values to *2* to create a Head-to-Head Match.  

## Thresholds

Thresholds are used to define how precise we want our matches to be, and for how long we want them to search for a Match. Thresholds use a combination of Periods of time and Match Types to calibrate the precision of our Match.

![](img/HowToMatchPlayers/3.png)  

### Match Types

A Match is built upon the different types of range criteria for the common attribute (i.e. skill level) that we want to match Players on. There are 3 different types of range criteria that can be used to fine-tune your Matches which make them more precise in matching Players with similar attributes:

* *Absolute* \- Match Players that fall between the specified minimum and maximum range of absolute values. Example: the first Period in the screenshot above will only match two Players who have a skill level between the values of 19 and 21.
* *Relative* \- Find a match between two Players where their values are no wider apart than the specified minimum and maximum values. Example: If Player 1 submits a *[MatchmakingRequest*](https://api.gamesparks.net/?jsonsdk#matchmakingrequest) with a skill level of X, Player 1 will only be matched to another Player who has a skill level 3 greater than or 3 less than X.
* *Percentage* \- Similar to Relative, find a match between Players where their values are no wider apart than the specified minimum and maximum percentage values. Example: If Player 1 submits a *MatchmakingRequest* with a skill level of X, Player 1 will only be matched to another Player who has a skill level between 25 percent less than and 50 percent greater than X.
* *Accept Min. Players* \- Selecting this for a particular threshold instructs the Match to match all the Players it has currently found after that selected threshold period is complete, on the condition that the number of Players found and matched is more than or equal to the value in the *Min. Players* field. If it hasn't found enough Players according to this value, the *Accept Min. Players* value is ignored and the Match continues to find Players in the next threshold.

**Remember!  If *Accept Min. Players* is not selected for any threshold, and there aren't enough Players found in the Match to reach the *Max. Players* value, no Match will be found, even if there are more Players than the *Min. Players* value.**

### Periods of time

We can specify how long we want to look for a Match Type before giving up. This can be done by creating Periods of time where we specify the Type on which we should match Players.

We can create multiple Threshold periods during one Match and in those Periods of time, we can specify different Types on which we should match Players. In my example above, I have 3 Thresholds, all with different Periods of time (in seconds). Once the *MatchmakingRequest* is executed, if the first Period does not find a suitable match, the following periods will continue to subsequently find a match until their duration has expired. By having a combination of longer and shorter Periods, we can fine-tune our Match criteria to be stricter or relaxed as the time duration of the Match progresses.

In my example in the screenshot above, my first Threshold will try to find a match based on an *Absolute* Match Type for *10* seconds. My second and third Thresholds will try to find a *Relative *match for *20* seconds and a *Percentage* match for *30* seconds respectively, before the Match ends.  

### Quick or Precise Matching?

Currently, Matches become more precise with an increased number of Thresholds.

For example, I have a simple Head-to-Head Match with 1 Threshold that has a minimum Relative value of *1 *and a maximum Relative value of *5.* If Player *1* submits a *MatchmakingRequest * first and has a skill of *15,* and Player *2* submits a *MatchmakingRequest *and has a skill of *20,  *there will be no Match even though Player *1*'s maximum Threshold matches Player *2*'s skill using these Threshold values, no reverse-matching occurs because Player *2*'s minimum Threshold value wouldn't match Player *1*'s skill.

However, more precise matches can be achieved simply by adding more Thresholds.

### Examples

In a more precise Head-to-Head Match, using Thresholds like the ones on *MULTI_MCH* above, would return a more accurate Match between Players than the previous example.

If Players *1*, *2* and *3* had skills of *20*, *15*, and *17* respectively and submitted a *MatchmakingRequest* in that order, during the time of Player *1*'s first threshold period, Players *1* and *3* would be matched based on the second (Relative) Match Type.

If Players *1*, *2* and *3* had skills of *20*, *15*, and *16* respectively and submitted a *MatchmakingRequest* in that order, during the time of Player *1*'s first threshold period, Players *2* and *3* would be matched based on the second (Relative) Match Type.

If Players *1*, *2* and *3* had skills of *20*, *15*, and *16* respectively, and Player's *2* and *3* submitted a *MatchmakingRequest* in that order, during the time of Player 1's *second* threshold period, Players *1* and *3* would again be matched based on the *third* (Percent) Match Type.  

## Multiplayer Matching

To match multiple Players, we will use the [*MatchmakingRequest*](https://docs.gamesparks.net/documentation/request-api/challenges-request-api/matchmakingrequest) in the *Test Harness*.  

*5.* In the *Test Harness*, authenticate 4 Players (in separate browser tabs) and have them each submit a *MatchmakingRequest* within 10 seconds so that all Players can attempt to match each other in their first threshold period.

Players *1*, *2*, *3* and *4* should have a skill of *16*, *21*, *19* and *22* respectively.

```
{
 "@class": ".MatchmakingRequest",
 "matchGroup": "group1",
 "matchShortCode": "MULTI_MCH",
 "skill": 16
}
```
```
{
 "@class": ".MatchmakingRequest",
 "matchGroup": "group1",
 "matchShortCode": "MULTI_MCH",
 "skill": 21
}
```
```
{
 "@class": ".MatchmakingRequest",
 "matchGroup": "group1",
 "matchShortCode": "MULTI_MCH",
 "skill": 19
}
```
```
{
 "@class": ".MatchmakingRequest",
 "matchGroup": "group1",
 "matchShortCode": "MULTI_MCH",
 "skill": 22
}
```
As you will notice, Players *2* and *3* will be matched almost immediately, because their skill values fall within the *first* (Absolute) threshold period.

Player 3 *MatchUpdatedMessage:*

```
{
 "@class": ".MatchUpdatedMessage",
 "messageId": "564db88ae4b03fe0ceb10a83",
 "notification": true,
 "summary": ".MatchUpdatedMessage",
 "participants": [
  {
   "online": true,
   "id": "5630b10ce4b0fdf2d2fa00d7",
   "displayName": "PLAYER TWO"
  },
  {
   "online": true,
   "id": "5630b113e4b0fdf2d2fa00f9",
   "displayName": "PLAYER THREE"
  }
 ],
 "matchShortCode": "MULTI_MCH",
 "matchGroup": "group1",
 "playerId": "5630b113e4b0fdf2d2fa00f9"
}
```

Around 10 seconds later, Player *4* will also be added to the Match, who will be matched based on his skill value falling within the *second* (Relative) threshold period.  As each Player is added to the Match, both them and the existing Players on the Match receive a [*MatchUpdatedMessage*](https://api.gamesparks.net/?jsonsdk#matchupdatedmessage).

Player 3 *MatchUpdatedMessage:*

```
{
 "@class": ".MatchUpdatedMessage",
 "messageId": "564db893e4b03fe0ceb10add",
 "notification": true,
 "summary": ".MatchUpdatedMessage",
 "participants": [
  {
   "online": true,
   "id": "564db393e4b03fe0ceb0d69e",
   "displayName": "PLAYER FOUR"
  },
  {
   "online": true,
   "id": "5630b10ce4b0fdf2d2fa00d7",
   "displayName": "PLAYER TWO"
  },
  {
   "online": true,
   "id": "5630b113e4b0fdf2d2fa00f9",
   "displayName": "PLAYER THREE"
  }
 ],
 "matchShortCode": "MULTI_MCH",
 "matchGroup": "group1",
 "playerId": "564db393e4b03fe0ceb0d69e"
}
```

Finally, Player *1* will be added to the Match, who is matched based on his skill value falling within the *third* (Percent) threshold period.  This will result in a *[MatchFoundMessage](https://api.gamesparks.net/?jsonsdk#matchfoundmessage).*

```
{
 "@class": ".MatchFoundMessage",
 "messageId": "564db8a1e4b03fe0ceb10d15",
 "notification": true,
 "summary": ".MatchFoundMessage",
 "participants": [
  {
   "achievements": [
    "100_ACH"
   ],
   "online": true,
   "id": "5630b091e4b0fdf2d2f9fbc2",
   "displayName": "PLAYER ONE"
  },
  {
   "online": true,
   "id": "564db393e4b03fe0ceb0d69e",
   "displayName": "PLAYER FOUR"
  },
  {
   "online": true,
   "id": "5630b10ce4b0fdf2d2fa00d7",
   "displayName": "PLAYER TWO"
  },
  {
   "online": true,
   "id": "5630b113e4b0fdf2d2fa00f9",
   "displayName": "PLAYER THREE"
  }
 ],
 "matchId": "564db886e4b03fe0ceb10a50",
 "matchShortCode": "MULTI_MCH",
 "matchGroup": "group1",
 "playerId": "564db393e4b03fe0ceb0d69e"
}
```

*6.* Repeat *Step 5*, but instead, change the skill value for Player *1* to be *15*. As Players *2, 3* and *4* are added to the Match, the average skill value in the Match increases and Player *1's* skill value will be too far away from the average value in the Match, even during the *third* (Percent) threshold period to match them.  A [*MatchNotFoundMessage*](https://api.gamesparks.net/?jsonsdk#matchnotfoundmessage) message will be returned to all Players requesting a Match, including those already in the Match:

```
{
 "@class": ".MatchNotFoundMessage",
 "messageId": "564dbf21e4b03fe0ceb14e59",
 "notification": true,
 "summary": ".MatchNotFoundMessage",
 "matchShortCode": "MULTI_MCH",
 "matchGroup": "group1",
 "playerId": "564db393e4b03fe0ceb0d69e"
}
```

As a result, no Match will be created. The Match we created earlier can be viewed using the [*MatchDetailsRequest*](https://api.gamesparks.net/?jsonsdk#matchdetailsrequest). 

Here is the request submitted by Player *4*:

```
{
 "@class": ".MatchDetailsRequest",
 "matchId": "564db886e4b03fe0ceb10a50"
}

<pre class="alert-info">{
 "@class": ".MatchDetailsResponse",
 "matchId": "564db886e4b03fe0ceb10a50",
 "opponents": [
  {
   "achievements": [
    "100_ACH"
   ],
   "online": true,
   "id": "5630b091e4b0fdf2d2f9fbc2",
   "displayName": "PLAYER ONE"
  },
  {
   "online": true,
   "id": "5630b10ce4b0fdf2d2fa00d7",
   "displayName": "PLAYER TWO"
  },
  {
   "online": true,
   "id": "5630b113e4b0fdf2d2fa00f9",
   "displayName": "PLAYER THREE"
  }
 ],
 "playerId": "564db393e4b03fe0ceb0d69e",
 "scriptData": null
}
```

### Cancelling a Match Request

*7. * To cancel an ongoing *MatchmakingRequest*, use the *action* parameter in the request with the value, *cancel*.

```
{
 "@class": ".MatchmakingRequest",
 "action": "cancel",
 "matchShortCode": "MULTI_MCH"
}
```

This will cancel a *MatchmakingRequest* that has not yet received any Match message.
