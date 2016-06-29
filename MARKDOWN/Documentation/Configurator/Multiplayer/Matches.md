---
nav_sort: 2
src: /Documentation/Configurator/Multiplayer/Matches.md
---

# Matches

Matchmaking allows players to be matched in real-time based on common attributes they share within a game. Using entirely customised threshold criteria and time-based rounds of matching, players can be strictly or loosely matched with an unlimited level of precision.

<q>**Tutorial!** You can find a detailed tutorial [here](/Tutorials/Multiplayer/Matching Players.md) where you can also follow a examples of how to create match configurations and use them to match players in the Test Harness.</q>

## Managing Match Configurations

The Multiplayer page in the Configurator section of the Portal, displays the list of Match configurations and allows you to create new Match configurations and edit or delete existing ones.

![](img/Matches/1.png)  

The icons (highlighted above) give you the following capabilities:

  * ![](/img/fa/plus.png) Add a new Match configuration.
  * ![](/img/fa/edit.png) Edit this Match configuration.
  * ![](/img/fa/trash.png) Delete this Match configuration.

## Creating a Match Configuration

To create a new Match, click the ![](/img/fa/plus.png) icon and you will be presented with the following overlay:

 ![](img/Matches/3.png)    

  * *Short Code* \- The Short Code is a mandatory field used to give the Match a unique identifier for use elsewhere in the Portal, in Cloud Code and the Test Harness.
  * *Name* \- The Name field is a mandatory field used as an identifier to help the user find the Match in the Portal.
  * *Description* \- The Description is a mandatory field which should be used to describe the Match.
  * *Min. Players* \- The minimum number of players required for a match to be found. This number will be used to find a match, only if a threshold is selected to accept this minimum number of players. Typically, a match would not be found unless the maximum number of players is found. You can use this option to ensure that a match is found on the basis of one of the match thresholds but for only the minimum number.
  * *Max. Players* \- The number of players required for a match to be found, if the minimum number of players is not accepted.
  * *Real Time* \- Select for a Real-Time match.
  * *Realtime Script* \- For a Real-Time match, you can select a Realtime script, which will be run on the Real-Time server when the Real-Time session starts. See the Realtime scripts section [here](/Documentation/Configurator/Cloud Code.md).
  * *Drop In/Drop Out* \- Select for a Drop in/Drop out match. In this type of match, the player list found for the match doesn't remain fixed after the match is made. Players that meet all of the matching criteria can enter or leave the match. Constraints:
    * The number of players can change but it cannot exceed the configured maximum number of players for the match.
    * If all players drop out, then the match is deleted.
  * For *Drop In/Drop Out* matches:
    * *Player disconnect delay in seconds* \- The number of seconds after a match is found before a player in the match who disconnects is removed from the match. If you do not enter a value or enter zero, then a player in the match who disconnects is removed instantly.
    * *Expire in seconds* \- The number of seconds after a match is made that players can drop in or drop out. If you do not enter a value or enter zero, the drop in/drop out period for the match doesn't expire.
  * *Manually match players* \- For custom completion of the matching process. Select this if you do not want the match to complete automatically when all matching criteria have been met, but want to use your own custom mechanism to complete the match. The platform will find players that meet the matching criteria for you, but you control the choice of which players are put in the match.
  * *Thresholds*:
    * *Period (seconds)* \- The period of time that a Threshold should look for a match based on that criteria.
    * *Type* \- The type of range calculation to use when looking for a match.  These can be *Absolute*, *Relative*, and *Percent*.
    * *Min/Max* \- The minimum and maximum values used for the type of range calculation used in the Threshold.
    * *Accept Min. Players* \- Select this option for a Threshold, if you want a match to be made on the basis of the threshold for the minimum number of players and not have to wait until the maximum number of players are found that fall within the threshold range.

<q>**Note:** Users with pre-existing Match configuration created before November 2015 will see the following attribute on the pre-existing configuration ONLY.  Any newly-created configuration will be visible as above.</q>

  * *Max Distance (metres)* \- The maximum distance to look for players based on that type of Threshold.
