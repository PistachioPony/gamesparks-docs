---
nav_sort: 5
src: /Documentation/Configurator/Leaderboards.md
---

# Leaderboards

Leaderboards are typically restricted to tracking and reporting the leading players in a game. GameSparks Leaderboards offer you a much wider and flexible scope, both for tracking comparisons within your player pool and for controlling how comparisons are displayed in-game to the players:
* **Highly Configurable** - Keep track of any comparisons of player performance and then support artifacts in-game that flexibly display this information in a meaningful form to players. This allows support for complex, contextual displays of information about other players and also provides the framework for many social and competitive features.
* **Highly Performant** - Our internal ranking and sorting algorithms allow new scores to be added to Leaderboards with 10m+ entries and have a new rank calculated within milliseconds.
* **Driven by Running Totals** - Leaderboards consume data from running totals and can also perform calculations on grouped running totals, allowing you to further transform the data from the running total into a list of scores of the values that you want. A single Leaderboard can consume data from multiple running totals (and in turn, from multiple Events). This allows for some complex Leaderboards, such as a Leaderboard with a halfway score and a final score in the same list. You can achieve this without having to worry about recording the halfway score during the game. Simply send the events when they happen and the platform does the rest!
* **Partition** - You can partition Leaderboards, which allows you to set up a single Leaderboard configuration and have it automatically create new Leaderboards when a particular value changes. A good example here is a level Leaderboard, where the rules are the same for the Leaderboard at each level. You tell the Leaderboard to partition by level and the rest is done for you. Far better than creating 100 separate Leaderboard configurations to represent each level!
* **Social Ranking** - Not only can Leaderboards provide instant rankings, but we can filter these based on your connection to a wide range of available social networks, such as ranking you against your socially networked friends.


## Managing Leaderboard configurations

The Configurator Leaderboard page displays the list of Leaderboards and allows you to create new Leaderboards and edit or delete existing ones.

![](img/Leaderboards/1.png)

The icons (highlighted above) give you the following capabilities:

  * ![](/img/fa/plus.png) Add a new Leaderboard.
  * ![](/img/fa/edit.png) Edit this Leaderboard.
  * ![](/img/fa/trash.png) Delete this Leaderboard.

## Creating a new Leaderboard configuration

Click the ![](/img/fa/plus.png) icon to create a new Leaderboard.

![](img/Leaderboards/2.jpg)

  * *Short Code* \-The Short Code is a mandatory field used to give the Leaderboard a unique identifier for use elsewhere in the Portal and in Cloud Code.
  * *Name* \-The Name field is a mandatory field used as an identifier to help the user find the Leaderboard in the Portal.
  * *Description* \-The Description is a mandatory field which should be used to describe the purpose of the Leaderboard.
  * *Type* \- The type of Leaderboard to be created. Leaderboards can be Team or Player based.
  * *Update Schedule* \-The rate at which the GameSparks platform will update the Leaderboard data.
    * Real-time \- the Leaderboard data is updated in real-time.
    * Reset Daily \- the Leaderboard data is reset each day.
    * Reset Weekly \- the Leaderboard data is reset each week.
    * Reset Monthly \- the Leaderboard data is reset each month.
    * Calculate Daily \- the Leaderboard data is updated every day.
    * Calculate Weekly \- the Leaderboard data is updated every week.
    * Calculate Monthly \- the Leaderboard data is updated every month.
  * *High Score Notifications* \- A flag to indicate whether a NewHighScoreMessage should be sent to the user when they submit a new high score.
  * *Social Notifications* \- A flag to indicate whether a SocialRankChangedMessage should be sent to friends when their scores are beaten.
  * *Top N Notifications* \- Whether a GlobalRankChangedMessage should be sent to players when their scores are beaten (if they are within the Top N Threshold).
  * *Top N Threshold* \- Which global positions in the Leaderboard should be notified when they are beaten.

### Create Leaderboard fields

Each Leaderboard configuration has a list of fields. Each field refers to an Event Attribute / Running Total Summary. Press the icon on the Edit Leaderboard dialog to add fields to a Leaderboard.

![](img/Leaderboards/3.jpg)

  * *Running Total* \- Contains a list of your Running Totals.
  * *Summary* \- Contains the list of Running Total Summaries that are related to the chosen Running Total.
  * *Filter Type* \- Allows you to select a filter which incoming Event Attribute values will be checked against before being entered in to the Leaderboard.
  * *Filter Value* \- Allows you to specify a value for the given filter type.
  * *Sort* \- Controls how this field affects the ordering of the Leaderboard if at all.
  * *Group* \- If the chosen Running Total Summary has a default calculation value of *Grouped* this field will allow you to select how the Leaderboard data should be grouped. Values available are:
    * MIN - Lowest entry
    * MAX - Highest entry
    * SUM - Sum of the entries
    * COUNT - Number of entries
    * RANGE - Difference between MIN and MAX
    * PARTITION - Partitions the Leaderboard on this Entry, more on that [here](/Tutorials/Social Features/Partitioning Leaderboards.md).
