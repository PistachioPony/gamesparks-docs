---
src: /API Documentation/Request API/Multiplayer/MatchmakingRequest.md
---

# MatchmakingRequest

*View interactive version <a href="https://api.gamesparks.net/#matchmakingrequest" target="_apidocs">here</a>*


Register this player for matchmaking, using the given skill and matchShortCode.

Players looking for a match using the same matchShortCode will be considered for a match, based on the matchConfig.

Each player must match the other for the match to be found.

If the matchShortCode points to a match with realtime enabled, in order to minimise latency, the location of Players and their proximity to one another takes precedence over their reciprocal skill values.


## Request Parameters

Parameter | Required | Type | Description
--------- | -------- | ---- | -----------
action | No | string | The action to take on the already in-flight request for this match. Currently supported actions are: 'cancel'
matchGroup | No | string | Optional. Players will be grouped based on the distinct value passed in here, only players in the same group can be matched together
matchShortCode | Yes | string | The shortCode of the match type this player is registering for
skill | No | number | The skill of the player looking for a match

## Response Parameters


A response to a matchmaking request

Parameter | Type | Description
--------- | ---- | -----------
scriptData | ScriptData | A JSON Map of any data added either to the Request or the Response by your Cloud Code

## Nested types

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Parameter | Type | Description
--------- | ---- | -----------
myKey | string | An arbitrary data key
myValue | JSON | An arbitrary data value.

## Error Codes

Key | Value | Description
--------- | ----------- | -----------
skill | may not be null | skill must be provided
matchShortCode | may not be null | matchShortCode must be provided
matchShortCode | NOT_FOUND | No matchConfig was found with the given matchShortCode
match | NOT_FOUND | No match was found for the current player

## Code Samples

<h3>C#</h3>
```cs
	using GameSparks.Api;
	using GameSparks.Api.Requests;
	using GameSparks.Api.Responses;
	...
	new MatchmakingRequest()
		.SetAction(action)
		.SetMatchGroup(matchGroup)
		.SetMatchShortCode(matchShortCode)
		.SetSkill(skill)
		.Send((response) => {
		GSData scriptData = response.ScriptData; 
		});

```

### ActionScript 3
```actionscript
	import com.gamesparks.*;
	import com.gamesparks.api.requests.*;
	import com.gamesparks.api.responses.*;
	import com.gamesparks.api.types.*;
	...
	
	gs.getRequestBuilder()
	    .createMatchmakingRequest()
		.setAction(action)
		.setMatchGroup(matchGroup)
		.setMatchShortCode(matchShortCode)
		.setSkill(skill)
		.send(function(response:com.gamesparks.api.responses.MatchmakingResponse):void {
		var scriptData:ScriptData = response.getScriptData(); 
		});

```

### Objective-C
```objectivec
	#import "GS.h"
	#import "GSAPI.h"
	...
	GSMatchmakingRequest* request = [[GSMatchmakingRequest alloc] init];
	[request setAction:action;
	[request setMatchGroup:matchGroup;
	[request setMatchShortCode:matchShortCode;
	[request setSkill:skill;
	[request setCallback:^ (GSMatchmakingResponse* response) {
	NSDictionary* scriptData = [response getScriptData]; 
	}];
	[gs send:request];

```

### C++
```cpp

	#include <GameSparks/generated/GSRequests.h>
	using namespace GameSparks::Core;
	using namespace GameSparks::Api::Responses;
	using namespace GameSparks::Api::Requests;
	...
	
	void MatchmakingRequest_Response(GS& gsInstance, const MatchmakingResponse& response) {
	GSData scriptData = response.getScriptData(); 
	}
	......
	
	MatchmakingRequest request(gsInstance);
	request.SetAction(action)
	request.SetMatchGroup(matchGroup)
	request.SetMatchShortCode(matchShortCode)
	request.SetSkill(skill)
	request.Send(MatchmakingRequest_Response);
```

### Java
```java
import com.gamesparks.sdk.api.autogen.GSRequestBuilder.MatchmakingRequest;
import com.gamesparks.sdk.api.autogen.GSResponseBuilder.MatchmakingResponse;
import com.gamesparks.sdk.api.autogen.GSTypes.*;
import com.gamesparks.sdk.api.GSEventListener;

...
gs.getRequestBuilder().createMatchmakingRequest()
	.setAction(action)
	.setMatchGroup(matchGroup)
	.setMatchShortCode(matchShortCode)
	.setSkill(skill)
	.send(new GSEventListener<MatchmakingResponse>() {
		@Override
		public void onEvent(MatchmakingResponse response) {
			GSData scriptData = response.getScriptData(); 
		}
	});

```

### Cloud Code
```javascript

	var request = new SparkRequests.MatchmakingRequest();
	request.action = ...;
	request.matchGroup = ...;
	request.matchShortCode = ...;
	request.skill = ...;
	var response = request.Send();
	
var scriptData = response.scriptData; 
```


