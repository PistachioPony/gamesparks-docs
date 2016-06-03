---
src: Documentation/Key Concepts/Authentication.md
---

# Authentication

Before a player can perform any operations they need to authenticate with the platform. There are a few authentication options, and some can be used in combination with others. These options are described below.

## Username / Password Authentication

Using RegistrationRequest you can create player with a username / password / displayName combination. If you use this method then the player can sign in on any device with the same credentials and will be logged in and their history will be available. Once a player has registered using RegistrationRequest they can use the same userName / password combination with AuthenticationRequest to login to the platform.

## Device Authentication

Perhaps you don't want to force your players to actively login. In these instances we still need the ability to identify the device that is being used so we can persist data against the player. To do this there is the ability to perform device authentication. This process registers an identifier (implementation dependent on platform) of the device and creates a stub player on the platform.

If you use device authentication, each time the device authenticates it will be identified as the same player and you will be able to view previous high scores, or use the same playerId in your code.

When using device authentication, there is no display name stored against the player. If you are using leaderboards, the displayName field of each leaderboard entry will be blank for these users. You can set a displayName against these anonymous players using ChangeUserDetailsRequest, which will set the displayName of the player and also update all leaderboard to contain the correct displayName.

## Social Authentication

If you don't want players to create a userName / password combination you can delegate authentication to one of the social providers. Currently these are:

* [Amazon](/?p=5778)
* [Facebook](/?p=2222)
* [Google Plus](/?p=5555)
* [Steam](/?p=5663)
* [Twitter](/?p=2224)
* [XBOX Live](/?p=6024)

These methods create a player on the platform, and also get their list of friends from the provider. This list of friends can then be used for linking players with their friends who also play your game. There are some rules that come into play when the player is already authenticated, or the social profile is already in use:

* If the player is already authenticated with one of the other methods, and the social profile is not already linked to another account, the social profile will be linked to the current player.
* If the player is already authenticated with one of the other methods, but the social profile is already linked to another player, the client will be logged out of the current account and re-authenticated with the player the social profile is linked to.
* If the player is not already authenticated, and the profile is not already in use, a new player record is created and linked to the social profile.
