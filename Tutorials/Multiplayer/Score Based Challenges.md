# Score Based Challenges

## Introduction

One of the most basic ways to win the challenge is to score the highest, or the lowest depending on what your score represents. In this tutorials, we will show examples of how to set up a challenge which ranks players on highest score and a challenge which ranks players on lowest score.  

## The Setup

 

### Event

Create an event. In that event create an attribute of data type Number.  If you want the challenge to be won for:

  * Highest Score: Set the attribute's 'Default Calc' to Maximum.
  * Lowest Score: Set the attribute's Default Calc to Minimum.

![](/img/ScoreBasedChallenges/1.jpg)
 

### Running Total (For Lowest score ONLY)

Create a running total. Link the running total to the event that you created for the challenge using the event drop down list. Add a new attribute and from the drop down list select the attribute you created for the event. From the summary type drop down menu select Minimum.

![](/img/ScoreBasedChallenges/2.jpg)
 

### Leaderboard

Create a leaderboard for your challenge.  If you want the challenge to be won for:

  * Highest Score: Don't do anything else to the leaderboard.
  * Lowest Score: Add a new running total. From the drop down list. Change the sorting to ASC.

![](/img/ScoreBasedChallenges/3.jpg)
 

### The challenge

Select your leaderboard from the leaderboard drop down list.  Optionally you can:

  * Make the challenge turn based by switching the turn base button on and assign a Turn/Attempt consumer event. (When this event is called using challenge event log it will consume a turn for the player which called it.)
  * Make the challenge achievement based by choosing the achievement from the drop down list. Elaborated tutorial here.

![](/img/ScoreBasedChallenges/4.jpg)
