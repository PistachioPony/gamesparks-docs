---
src: /Tutorials/Cloud Code and the Test Harness/Working with the Game REST API.md
---

# Game REST API

The game REST API allows you to retrieve, create or update the full configuration for your game in JSON format.

## *Retrieving a game configuration*

The configuration for a game can be retrieved using the following URL:

*GET: /rest/games/{gameApiKey}*

### Parameters:

  * *gameApiKey* \- is the API key of you game and can be found on the overview page of the Portal Configurator

### Example Request

*GET: https://portal.gamesparks.net/rest/games/161bhegV3Qde*

### Example Response

```
    {
      "name": "Time Pilot 2014",
      "description": "A top down shooter",
      "facebookAppId": "548892405185305",
      "facebookSecret": "32bd462a6f9d9363c5190306ac12beb0",
      "signupBonus1": 10,
      "signupBonus2": 0,
      "signupBonus3": 0,
      "signupBonus4": 0,
      "signupBonus5": 0,
      "signupBonus6": 0,
      "pushConfiguration": {
        "bundleId": null,
        "devPushCertificate": null,
        "devPushCertificateName": null,
        "devCertPassword": null,
        "prodPushCertificate": null,
        "prodPushCertificateName": null,
        "prodCertPassword": null,
        "useIosProdCert": false,
        "useIosSandboxVerification": false,
        "gcmApiKey": null,
        "googlePlayPublicKey": null,
        "packageSid": null,
        "secretKey": null,
        "includeInPush": null,
        "pushConfigurationMessages": {}
      },
      "apiKey": "161bhegV3Qde",
      "events": [],
      "leaderboards": [],
      "eventProcessors": [],
      "aggregations": [],
      "achievements": [],
      "challenges": [],
      "virtualGoods": []
    }
```

### *Creating a game configuration*

The configuration for a game can be created using the following URL:

*POST: /rest/games*

### Payload

The payload is a JSON representation of the game configuration.

#### Game

This is the root of the game configuration structure. The fields of type object and array and described in the sections following this one. Mandatory fields:

  * name
  * description

```
    {
      "name": string,
      "description": string,
      "facebookAppId": string,
      "facebookSecret": string,
      "signupBonus1": number,
      "signupBonus2": number,
      "signupBonus3": number,
      "signupBonus4": number,
      "signupBonus5": number,
      "signupBonus6": number,
      "pushConfiguration": object,
      "events": array,
      "leaderboards": array,
      "eventProcessors": array,
      "aggregations": array,
      "achievements": array,
      "challenges": array,
      "virtualGoods": array
    }
```
#### PushConfiguration

Contains push notification configuration for the various third party platform providers such as Google and Apple.

```  
    {
      "bundleId": string,
      "devPushCertificate": string,
      "devPushCertificateName": string,
      "devCertPassword": string,
      "prodPushCertificate": string,
      "prodPushCertificateName": string,
      "prodCertPassword": string,
      "useIosProdCert": boolean,
      "useIosSandboxVerification": boolean,
      "gcmApiKey": string,
      "googlePlayPublicKey": string,
      "packageSid": string,
      "secretKey": string,
      "includeInPush": boolean,
      "pushConfigurationMessages": {
        "ChallengeWithdrawnMessage": {
         * "messageClass": "ChallengeWithdrawnMessage",*
          "pushNotify": boolean,
          "enabled": boolean,
          "gameSummary": boolean,
          "messageTemplate": string
        },
      "ChallengeDrawnMessage": {
       * "messageClass": "ChallengeDrawnMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeTurnTakenMessage": {
        *"messageClass": "ChallengeTurnTakenMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeAcceptedMessage": {
       * "messageClass": "ChallengeAcceptedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "SocialRankChangedMessage": {
       * "messageClass": "SocialRankChangedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeDeclinedMessage": {
       * "messageClass": "ChallengeDeclinedMessage",*
        pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ScriptMessage": {
        *"messageClass": "ScriptMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeExpiredMessage": {
        *"messageClass": "ChallengeExpiredMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
     "ChallengeWaitingMessage": {
       * "messageClass": "ChallengeWaitingMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
       },
     "ChallengeStartedMessage": {
       * "messageClass": "ChallengeStartedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "AchievementEarnedMessage": {
       * "messageClass": "AchievementEarnedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeChatMessage": {
       * "messageClass": "ChallengeChatMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeIssuedMessage": {
        *"messageClass": "ChallengeIssuedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeLostMessage": {
        *"messageClass": "ChallengeLostMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "FriendMessage": {
       * "messageClass": "FriendMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "GlobalRankChangedMessage": {
       * "messageClass": "GlobalRankChangedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeWonMessage": {
       * "messageClass": "ChallengeWonMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "ChallengeChangedMessage": {
       * "messageClass": "ChallengeChangedMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "UploadCompleteMessage": {
     *   "messageClass": "UploadCompleteMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        },
      "NewHighScoreMessage": {
       * "messageClass": "NewHighScoreMessage",*
        "pushNotify": boolean,
        "enabled": boolean,
        "gameSummary": boolean,
        "messageTemplate": string
        }
      }
    }
```

#### Event

Contains Event configuration data including an array of (optional) Event Attributes.  There must be a corresponding Aggregation object with the same short code as the Event.

```    
    {
      *"name": string,
      "description": string,
      "shortCode": string,*
      "eventAttributes": [
        {
         * "name": string,
          "shortCode": string,*
         * "dataType": "string|int|json",*
         * "defaultAggregationType": "SCRIPT|MAX|MIN|SUM|COUNT|GROUP",*
          "defaultValue": string
        }
      ]
    }
```

#### Leaderboard

Contains Leaderboard configuration data including an (optional) array of Leaderboard Orders. The Leaderboard Order field aggregationAttributeRef is a special type of field that acts as a reference to this Leaderboard Order's corresponding Aggregation Attribute.  The syntax of this field is:

game.aggregations[<Aggregation Attribute Short Code>].aggregationAttributes[Aggregation Attribute index]

E.g. game.aggregations[EVT1].aggregationAttributes[0]

```
{
 * "name": string,
  "description": string,
  "shortCode": string,*
  "socialNotificationsEnabled": boolean,
  "topNNotificationsEnabled": boolean,
  "topNThreshold": number,
 * "updateFrequency": "NEVER|REALTIME|DAILY|WEEKLY|MONTHLY",*
  "leaderboardOrders": [
    {
     * "filterType": "*|=|!=|>|<|>=|<=",*
      "filterValue": string,
     * "sort": "ASC|DESC|NONE"*,
     * "calcType": "MIN|MAX|SUM|COUNT|GROUP",*
    *  "aggregationAttributeRef": reference*
    }
  ]
}
```

#### EventProcessor (Cloud Code)

Contains Cloud Code script configuration data.  Note that script field must contain valid Javascript that the server can compile.

```
{
  "type": "event|challengeEvent|request|response|userMessage|message|modules|systemModules",
  *"binding": string,
  "script": string*
}
```

#### Aggregation (Running Total)

Contains Running Total configuration data including an array of (optional) Aggregation Attributes.  If the short code matches the Event short code and there is a corresponding Event in the game configuration a 'system' running total will be created otherwise a 'user' Running Total will be created.

```
{
 * "name": string,
* * "shortCode": string,*
  "eventShortCode": string,
 *"groupBy": string,*
  "aggregationAttributes": [
    {
      "filterType": "*|=|!=|>|<|>=|<=",
      "filterValue": string,
      "calcType": "MAX|MIN|SUM|COUNT",
      "eventAttributeShortCode": string
    }
  ]
}
```

#### Achievement

Contains Achievement configuration data including a array of (optional) Achievement Triggers.

```
{
 *"name": string,
  "description": string,
  "shortCode": string,*
  "leaderboardShortCode": string,
  "virtualGoodAwardShortCode": string,
  "currency1Award": number,
  "currency2Award": number,
  "currency3Award": number,
  "currency4Award": number,
  "currency5Award": number,
  "currency6Award": number,
  "achievementTriggers": [
    {
      "leaderboardOrderShortCode": string,
      "filterType": "*|=|!=|>|<|>=|<=",
      "filterValue": null
    }
  ]
}
```
#### Challenge

Contains Challenge configuration data.

```
{
  *"name": string,
  "description": string,
  "shortCode": string,*
  "leaderboardShortCode": string,
  "achievementShortCode": string,
  "turnBased": boolean,
  "tags": string,
  "attemptConsumers": string
}
```

#### VirtualGood

Contains Virtual Good configuration data.  Virtual Goods can represent either a virtual item or a currency pack, this is indicated by the 'type' field.

```
{
 * "name": string,
  "description": string,
  "shortCode": string,*
  "image": string,
  "type": "VGOOD|CURRENCY",
  "tags": string,
  "currency1Cost": number,
  "currency2Cost": number,
  "currency3Cost": number,
  "currency4Cost": number,
  "currency5Cost": number,
  "currency6Cost": number,
  "googlePlayProductId": string,
  "iosAppStoreProductId": string,
  "maxQty": number,
  "wp8StoreProductId": string
}
```

### Example Request

*POST: https://portal.gamesparks.net/rest/games*

```
{
  "name": "Time Pilot 2014",
  "description": "A top down shooter",
  "facebookAppId": null,
  "facebookSecret": null,
  "signupBonus1": 0,
  "signupBonus2": 0,
  "signupBonus3": 0,
  "signupBonus4": 0,
  "signupBonus5": 0,
  "signupBonus6": 0,
  "events": [],
  "leaderboards": [],
  "eventProcessors": [],
  "aggregations": [],
  "achievements": [],
  "challenges": [],
  "virtualGoods": []
}
```

### Example Response

```
{
  "name": "Time Pilot 2014",
  "description": "A top down shooter",
  "facebookAppId": null,
  "facebookSecret": null,
  "signupBonus1": 0,
  "signupBonus2": 0,
  "signupBonus3": 0,
  "signupBonus4": 0,
  "signupBonus5": 0,
  "signupBonus6": 0,
  "pushConfiguration": {
    "bundleId": null,
    "devPushCertificate": null,
    "devPushCertificateName": null,
    "devCertPassword": null,
    "prodPushCertificate": null,
    "prodPushCertificateName": null,
    "prodCertPassword": null,
    "useIosProdCert": false,
    "useIosSandboxVerification": false,
    "gcmApiKey": null,
    "googlePlayPublicKey": null,
    "packageSid": null,
    "secretKey": null,
    "includeInPush": null,
    "pushConfigurationMessages": {}
  },
  "apiKey": "184rNgsTGBSg",
  "events": [],
  "leaderboards": [],
  "eventProcessors": [],
  "aggregations": [],
  "achievements": [],
  "challenges": [],
  "virtualGoods": []
}
```

### *Updating a game configuration*

The configuration for a Game can be updated using the URL below.  The processing of child arrays such as the 'events' and 'leaderboards' fields will result in the creation of new items, updates to any existing items and the removal of any missing items.

*POST: /rest/games/{gameApiKey}*

### Parameters:

*gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator

### Payload

The payload is the same JSON structure as for creating a game configuration.  

### *Changing the Owner of a Game to another Collaborator*

The Owner of a Game can be changed using the URL below.  The user specified in the payload *must* already be a Collaborator on the Game.

*POST: /rest/games/{gameApiKey}/owner*

### Parameters:

*gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator

### Payload

*{"username" : "_[username]_"}* - you must specify the username value of the JSON name/value pair.  

### *Errors*

If an error occurs with any of the game REST API calls an error response will be returned containing a response code and a message.

```
{
 "responseCode": number,
 "errorMessage": string
}
```

#### Response code meanings


| Code  | Description  |
|---|---|
|-1|General Error.  See the error message for details.|
|1|Resource not found error. A referenced resource could not be found.  See the error message for details. |
|2|Short code not unique error.  Short code must be unique for a given type of game configuration object.  |
|3|Invalid aggregation type for data type of ‘string’ in event attribute. Valid types are: MIN, MAX, AVG and SUM.  |
|4|Unknown data type error. Valid values are: string, int, json.   |
|5|Invalid aggregation type for data type of ‘JSON’ in event attribute. Valid type is: SCRIPT.   |
|6|Item in use error.  Occurs when you try to remove an item that is in use elsewhere in the configuration.  |
|7|Security error.  Check the API key and Basic Auth credentials that you are using.   |
|8|IO error. A failed or interrupted I/O opperation has occured.   |
|9|Unknown short code error.  The item referenced by short code could not be found.   |
|10|Validation error.  A violation of the game domain model’s constraints has occured.  |
