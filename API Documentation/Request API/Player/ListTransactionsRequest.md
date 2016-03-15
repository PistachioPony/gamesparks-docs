
# ListTransactionsRequest


Returns a list of the current player's transaction history.


## Request Parameters

Parameter | Required | Type | Description
--------- | -------- | ---- | -----------
dateFrom | No | date | Optional date constraint to list transactions from
dateTo | No | date | Optional date constraint to list transactions from
entryCount | No | number | The number of items to return in a page (default=50)
include | No | string | An optional filter that limits the transaction types returned
offset | No | number | The offset (page number) to start from (default=0)

## Response Parameters


A response listing transactions for the player

Parameter | Type | Description
--------- | ---- | -----------
scriptData | ScriptData | A JSON Map of any data added either to the Request or the Response by your Cloud Code
transactionList | JSON[] | A list of JSON objects containing player transactions

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
	new ListTransactionsRequest()
		.SetDateFrom(dateFrom)
		.SetDateTo(dateTo)
		.SetEntryCount(entryCount)
		.SetInclude(include)
		.SetOffset(offset)
		.Send((response) => {
		GSData scriptData = response.ScriptData; 
		IList<GSData> transactionList = response.TransactionList; 
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
	    .createListTransactionsRequest()
		.setDateFrom(dateFrom)
		.setDateTo(dateTo)
		.setEntryCount(entryCount)
		.setInclude(include)
		.setOffset(offset)
		.send(function(response:com.gamesparks.api.responses.ListTransactionsResponse):void {
		var scriptData:ScriptData = response.getScriptData(); 
		var transactionList:Vector.<Object> = response.getTransactionList(); 
		});

```

### Objective-C
```objectivec
	#import "GS.h"
	#import "GSAPI.h"
	...
	GSListTransactionsRequest* request = [[GSListTransactionsRequest alloc] init];
	[request setDateFrom:dateFrom;
	[request setDateTo:dateTo;
	[request setEntryCount:entryCount;
	[request setInclude:include;
	[request setOffset:offset;
	[request setCallback:^ (GSListTransactionsResponse* response) {
	NSDictionary* scriptData = [response getScriptData]; 
	NSArray* transactionList = [response getTransactionList]; 
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
	
	void ListTransactionsRequest_Response(GS& gsInstance, const ListTransactionsResponse& response) {
	GSData scriptData = response.getScriptData(); 
	gsstl:vector<GSData> transactionList = response.getTransactionList(); 
	}
	......
	
	ListTransactionsRequest request(gsInstance);
	request.SetDateFrom(dateFrom)
	request.SetDateTo(dateTo)
	request.SetEntryCount(entryCount)
	request.SetInclude(include)
	request.SetOffset(offset)
	request.Send(ListTransactionsRequest_Response);
```

### Java
```java
import com.gamesparks.sdk.api.autogen.GSRequestBuilder.ListTransactionsRequest;
import com.gamesparks.sdk.api.autogen.GSResponseBuilder.ListTransactionsResponse;
import com.gamesparks.sdk.api.autogen.GSTypes.*;
import com.gamesparks.sdk.api.GSEventListener;

...
gs.getRequestBuilder().createListTransactionsRequest()
	.setDateFrom(dateFrom)
	.setDateTo(dateTo)
	.setEntryCount(entryCount)
	.setInclude(include)
	.setOffset(offset)
	.send(new GSEventListener<ListTransactionsResponse>() {
		@Override
		public void onEvent(ListTransactionsResponse response) {
			GSData scriptData = response.getScriptData(); 
			List<GSData> transactionList = response.getTransactionList(); 
		}
	});

```

### Cloud Code
```javascript

	var request = new SparkRequests.ListTransactionsRequest();
	request.dateFrom = ...;
	request.dateTo = ...;
	request.entryCount = ...;
	request.include = ...;
	request.offset = ...;
	var response = request.Send();
	
var scriptData = response.scriptData; 
var transactionList = response.transactionList; 
```


