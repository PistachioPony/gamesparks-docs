# Social Capabilities

The GameSparks platform allows you to make use of players' existing social media relationships to build a truly social gaming experience.

## Connect

The GameSparks platform exposes social API calls that allow you to connect your players with their social media profiles - for more information on setting this up see [Social Integration](/category/howtos/social-integration). This allows the GameSparks platform to get data about your players on your behalf, which gives the platform access to information such as friend lists. Connecting is the first step towards utilising the platform's social capabilities.

## Invite

Using the [ListInviteFriendsRequest](/?p=2251) you can get a list of friends for the current player who are not yet players in your game. You can use this to encourage your players to get their friends playing your game. This kind of social propagation is key in getting awareness of your game to spread virally.

## Match

Using the [ListGameFriendsRequest](/?p=2250) you can get a list of friends for the current player who are already players of your game. This allows you to match up players and encourage them to chat to their friends, and challenge each other.

## Chat

Using the [SendFriendMessageRequest](/?p=2255) you can send messages between two players that are friends. For more information on the messaging capabilities provided by the GameSparks platform see [Messaging](/?p=2577).

## Rank

Leaderboard data for players that are linked as friends will contain not only their global position within the leaderboard but also a social rank, relative only to their friends. This lets players compete against their friends as well as against the wider population. Achievements can be awarded based on social rankings, meaning players are competing against a much smaller population for those precious awards! For more information on leaderboards within the GameSparks platform see [Leaderboards](/?p=28).
