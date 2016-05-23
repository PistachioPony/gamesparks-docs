---
nav_sort: 2
---

# Using Authentication

## Introduction

Before a player can perform any operations they need to authenticate with the platform. There are a few authentication options, and some can be used in combination with others. The full list of Authentication Types can be found [here](..\..\Tutorials\Authentication and Player Profile\Authentication.html), however for this tutorial we'll be using basic username/password Registration and Authentication.

## Authenticating and Registering

![](img/UsingAuthentication/1.png)

To test your game and see if it is ready for Authentication, you will have to navigate to the [Test Harness](..\..\Tutorials\Cloud Code, and the Test Harness\Test Harness.html), Click *Authentication* and then *RegistrationRequest*. Then simply enter the desired registration details in the JSON builder for your player and hit Play. At this point you will see GameSparks receiving the [RegistrationRequest](https://docs.gamesparks.net/documentation/request-api/authentication-request-api/registrationrequest). When processed, the server will send you a [RegistrationResponse](https://docs.gamesparks.net/documentation/response-api/authentication-response-api/registrationresponse). Note: You might have to remove some additional or unwanted fields (that are auto-generated) to match the example and take note of the player you've just registered. This will be required for upcoming Getting Started tutorials.

![](img/UsingAuthentication/2.png)

Receiving a successful response is an indication of a successful registration. To validate this we can select the *AuthenticationRequest*, add our players' details into the JSON builder and after clicking Play, we will send an [AuthenticationRequest](/documentation/request-api/authentication-request-api/authenticationrequest) and receive an [AuthenticationResponse](https://docs.gamesparks.net/documentation/response-api/authentication-response-api/authenticationresponse). In addition to receiving a successful Response, you will also notice that you've received an *authToken* for the current players session.
 
You have now successfully Registered and Authenticated a player. The next tutorial will show you how to set up the SDK of your choice for authentication with GameSparks.      

## SDK Instructions

|[![](../img/URLogo.png)](Using Authentication\Unreal Authentication.html)   |[![](../img/UTLogo.png)](Using Authentication\unity Authentication.html)   |[![](../img/ASLogo.png)](Using Authentication\ActionScript Authentication.html)   |
|---|---|---|
