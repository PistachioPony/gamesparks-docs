---
nav_sort: 10
src: Documentation/Configurator/Matches.md
---

# Matches

Matchmaking allows Players to be matched in real-time based on common attributes they share within a game. Using entirely customised threshold criteria and time-based rounds of matching, Players can be strictly or loosely matched with an unlimited level of precision.

## Managing Matches

The Multiplayer page in the Configurator section of the Portal, displays the list of Matches and allows you to create new Matches and edit or delete existing ones.

![](img/Matches/1.png)  

The icons (highlighted above) give you the following capabilities:

  * [addIcon] Add a new Match.
  * [editIcon] Edit this Match.
  * [deleteIcon] Delete this Match.

## Creating a new Match

To create a new Match, select the *Add* (*+*) icon and you will be presented with the following overlay:

 ![](img/Matches/2.png)    

  * *Short Code* \- The Short Code is a mandatory field used to give the Match a unique identifier for use elsewhere in the Portal, in Cloud Code and the Test Harness.
  * *Name* \- The Name field is a mandatory field used as an identifier to help the user find the Match in the Portal.
  * *Description* \- The Description is a mandatory field which should be used to describe the Match.
  * *Number of Players* \- The number of Players required for a Match to be found.
  * *Period (seconds)* \- The period of time that a Threshold should look for a match based on that criteria.
  * *Type* \- The type of range calculation to use when looking for a match.  These can be *Absolute*, *Relative*, and *Percent*
  * *Min/Max* \- The minimum and maximum values used for the type of range calculation used in the Threshold.

**Users with pre-existing Match configuration created before November 2015 will see the following attribute on the pre-existing configuration ONLY, and will not see *Number of Players*.  Any newly-created configuration will be visible as above.***

  * *Max Distance (metres)* \- The maximum distance to look for players based on that type of Threshold.
