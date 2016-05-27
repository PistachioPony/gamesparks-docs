# Snapshot REST API

The GameSparks platform allows you to manage game snapshots via a REST interface, this is useful to allow you to control publishing between environments and have this managed by your own software. The REST endpoint requires Basic Auth, see [here](./GameSparks REST API.md) for details

## Create a Snapshot

A snapshot can be created using the following URL:

*GET: /rest/games/{gameApiKey}/snapshot/create/{description}*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.
* *description (optional)* The description for the snapshot. If not supplied a description will be generated using the current date/time

#### Example Request

*GET: https://portal.gamesparks.net/rest/games/44ujrP2BnudG/snapshot/create*

#### Example Response

  ```  
    {
     "id": "537f04fc4310ceb95a335990",
     "description": "23 May 2014 08:21:16 GMT",
     "created": "2014-05-23T08:21Z"
    }
```
## Copy a Snapshot to a new Game

A snapshot can be copied to a new game using the following URL

*GET: /rest/games/{gameApiKey}/snapshot/copy/{snapshotId}*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.
* *snapshotId* is the id of the snapshot to copy.

#### Example Request

*GET: /rest/games/44ujrP2BnudG/snapshot/copy/537efabe43102900233c7765*

#### Example Response

```    
    {
        "responseCode": 0,
        "errorMessage": null
    }
```

## Copy a Snapshot to an existing Game

A snapshot can be copied to an existing game using the following URL

*GET: /rest/games/{gameApiKey}/snapshot/copy/{snapshotId}/to/{targetApiKey}*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.
* *snapshotId* is the id of the snapshot to copy.
* *targetApiKey* is the API key of the game you want to copy the snapshot to.

#### Example Request

*GET: /rest/games/44ujrP2BnudG/snapshot/copy/537efabe43102900233c7765/to/57tcnMun8cj9*

#### Example Response

  ```  
    {
        "responseCode": 0,
        "errorMessage": null
    }
```

## List Snapshots for a Game

The list of snapshots for a game can be retrieved using the following URL

*GET: /rest/games/{gameApiKey}/snapshot/list*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.

#### Example Request

*GET: /rest/games/44ujrP2BnudG/snapshot/list*

#### Example Response

  ```  
    [
     {
     "id": "537f04fc4310ceb95a335990",
     "description": "23 May 2014 08:21:16 GMT",
     "created": "2014-05-23T08:21Z"
     },
     {
     "id": "537f040b43102c3fdaa6e310",
     "description": "23 May 2014 08:17:15 GMT",
     "created": "2014-05-23T08:17Z"
     },
     {
     "id": "537efabe43102900233c7765",
     "description": "some text",
     "created": "2014-05-23T07:37Z"
     }
    ]
```
## Delete a Snapshot

A snapshot can be deleted using the following URL

*GET: /rest/games/{gameApiKey}/snapshot/delete/{snapshotId}*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.
* *snapshotId* is the id of the snapshot to delete.

#### Example Request

*GET: /rest/games/44ujrP2BnudG/snapshot/delete/537f04fc4310ceb95a335990*

#### Example Response

  ```  
    {
     "responseCode": 0,
     "errorMessage": null
    }
```

Publish a Snapshot

## Publish a Snapshot

A snapshot can be published using the following URL

*GET: /rest/games/{gameApiKey}/snapshot/publish/{snapshotId}*

#### Parameters

* *gameApiKey* is the API key of you game and can be found on the overview page of the Portal Configurator.
* *snapshotId* is the id of the snapshot to publish.

#### Example Request

*GET: /rest/games/44ujrP2BnudG/snapshot/publish/537f04fc4310ceb95a335990*

#### Example Response

  ```  
    {
     "responseCode": 0,
     "errorMessage": null
    }
```

## *Errors*

If an error occurs with any of the snapshot REST API calls an error response will be returned containing a response code and a message.

```    
    {
     "responseCode": number,
     "errorMessage": string
    }
```

#### Response code meanings



|Code   |Description   |
|---|---|
|-1   |General Error. See the error message for details.   |
|1   |Snapshot not found. The snapshot id provided does not exist.   |
|2   |Cannot delete published snapshot.   |
|3   |Snapshot already published.   |
|7   |Security error. Check the API key and Basic Auth credentials that you are using.   |
|8   |IO error. A failed or interrupted I/O operation has occurred.   |
