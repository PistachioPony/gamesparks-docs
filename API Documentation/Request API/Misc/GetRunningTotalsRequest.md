
# GetRunningTotalsRequest


Get the aggregation data for a group of the player's friends given running total specified by short code.


## Request Parameters

Parameter | Required | Type | Description
--------- | -------- | ---- | -----------
friendIds | No | string[] | A friend id or an array of friend ids
shortCode | Yes | string | The short code of the running total

## Response Parameters


A response containing aggregation data

Parameter | Type | Description
--------- | ---- | -----------
runningTotals | JSON | A list of JSON objects representing the aggregation data
scriptData | ScriptData | A JSON Map of any data added either to the Request or the Response by your Cloud Code

## Nested types

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Parameter | Type | Description
--------- | ---- | -----------
myKey | string | An arbitrary data key
myValue | JSON | An arbitrary data value.


## Code Samples

<h3>C#</h3>
```cs
	using GameSparks.Api;
	using GameSparks.Api.Requests;
	using GameSparks.Api.Responses;
	...
	new GetRunningTotalsRequest()
		.SetFriendIds(friendIds)
		.SetShortCode(shortCode)
		.Send((response) => {
		GSData runningTotals = response.RunningTotals; 
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
	    .createGetRunningTotalsRequest()
		.setFriendIds(friendIds)
		.setShortCode(shortCode)
		.send(function(response:com.gamesparks.api.responses.GetRunningTotalsResponse):void {
		var runningTotals:Object = response.getRunningTotals(); 
		var scriptData:ScriptData = response.getScriptData(); 
		});

```

### Objective-C
```objectivec
	#import "GS.h"
	#import "GSAPI.h"
	...
	GSGetRunningTotalsRequest* request = [[GSGetRunningTotalsRequest alloc] init];
	[request setFriendIds:friendIds;
	[request setShortCode:shortCode;
	[request setCallback:^ (GSGetRunningTotalsResponse* response) {
	NSDictionary* runningTotals = [response getRunningTotals]; 
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
	
	void GetRunningTotalsRequest_Response(GS& gsInstance, const GetRunningTotalsResponse& response) {
	GSData runningTotals = response.getRunningTotals(); 
	GSData scriptData = response.getScriptData(); 
	}
	......
	
	GetRunningTotalsRequest request(gsInstance);
	request.SetFriendIds(friendIds)
	request.SetShortCode(shortCode)
	request.Send(GetRunningTotalsRequest_Response);
```

### Java
```java
import com.gamesparks.sdk.api.autogen.GSRequestBuilder.GetRunningTotalsRequest;
import com.gamesparks.sdk.api.autogen.GSResponseBuilder.GetRunningTotalsResponse;
import com.gamesparks.sdk.api.autogen.GSTypes.*;
import com.gamesparks.sdk.api.GSEventListener;

...
gs.getRequestBuilder().createGetRunningTotalsRequest()
	.setFriendIds(friendIds)
	.setShortCode(shortCode)
	.send(new GSEventListener<GetRunningTotalsResponse>() {
		@Override
		public void onEvent(GetRunningTotalsResponse response) {
			GSData runningTotals = response.getRunningTotals(); 
			GSData scriptData = response.getScriptData(); 
		}
	});

```

### Cloud Code
```javascript

	var request = new SparkRequests.GetRunningTotalsRequest();
	request.friendIds = ...;
	request.shortCode = ...;
	var response = request.Send();
	
var runningTotals = response.runningTotals; 
var scriptData = response.scriptData; 
```


