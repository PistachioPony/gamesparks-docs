---
src: Tutorials/Social Features/Time Based Leaderboards.md
---

# How to create time based Leaderboards

You can use the GameSparks platform to create Leaderboards that are based on time. Some examples of these are:

  * Highest Score in the last 30 days
  * Most improved in the last 7 days


To implement time based Leaderboards you will need to do some specific setup tasks, and this post aims to take you through the details of this.

We'll go through the process of creating a "Highest score in the last 30 days" Leaderboard, that is built once a month, but after reading this post you should be able to create other combinations for your own requirements.

## Creating the Event

To get started, we need to start tracking in our running total the day a particular score was made. We'll create a new event with a SCORE attribute, and another attribute to hold the day of the score.

![](img/TimeLDR/1.jpg)

You notice we've added a default value to the "DAY" attribute, the addition of this default value mean you do not need to pass a DAY attribute as part of the [LogEventRequest](https://docs.gamesparks.net/documentation/request-api/player-request-api/logeventrequest) and the platform will calculate it.

You also notice we are using an expression (starting with $). There are a few expressions available that allow you to auto calculate a value for the default, the one we are using is ${today} which will automatically resolve to the epoch time of midnight today.

## Creating the Running Total

Once we have the event configured we need to create a custom running total for this event, to allow us to have an entry for each player and day combination.

![](img/TimeLDR/2.jpg)

In this running total, note we've included "Day" in the Group section, this will cause the running total to keep a track of the players scores for each day.

## Creating the Leaderboard

We can now create the Leaderboard to consume the running total data we can configured. As it's a time based one we'll create a scheduled Leaderboard that runs once a month, and then only consumes data for the last 30 days when being built.

![](img/TimeLDR/3.jpg)

We've configured this Leaderboard to be built every month by setting "Update Schedule" to "Calculate monthly" and we've configured it to only consume the last 30 days by adding another expression into the "Filter Value" of ${today:minusDays(30)}.

When the Leaderboard is built, it will have a short code of HSL30D.SCHEDULED.YYYY-MM-DD where the date components are the date of the Leaderboard build.

With this process, each previous scheduled Leaderboard is preserved, and you can query for historical data using the date component of the short code.

When you make a [ListLeaderboardsRequest](https://docs.gamesparks.net/documentation/request-api/leaderboards-request-api/listleaderboardsrequest), each of the build Leaderboard will be returned in the Response so you can query which Leaderboards are available.

## Expressions

The current list of expressions available is

  * ${today} - The epoch time of midnight today.
  * ${now} - The current epoch time.
  * ${today:minusDays(N)} - The epoch time of midnight N days ago.
  * ${today:plusDays(N)} - The epoch time of midnight N days in the future.
