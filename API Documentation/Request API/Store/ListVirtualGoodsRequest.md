
# ListVirtualGoodsRequest


Returns the list of configured virtual goods.


## Request Parameters

Parameter | Required | Type | Description
--------- | -------- | ---- | -----------
tags | No | string[] | A filter to only include goods with the given tags. Each good must have all the provided tags.

## Response Parameters


A response containing the list of configured virtual goods.

Parameter | Type | Description
--------- | ---- | -----------
scriptData | ScriptData | A JSON Map of any data added either to the Request or the Response by your Cloud Code
virtualGoods | [VirtualGood[]](#virtualgood) | A list of JSON objects containing virtual goods data

## Nested types

### ScriptData

A collection of arbitrary data that can be added to a message via a Cloud Code script.

Parameter | Type | Description
--------- | ---- | -----------
myKey | string | An arbitrary data key
myValue | JSON | An arbitrary data value.

### VirtualGood

A nested object that represents the virtual good.

Parameter | Type | Description
--------- | ---- | -----------
WP8StoreProductId | string | The Windows Phone 8 productId of the item.
amazonStoreProductId | string | The Amazon Store productId of the item.
currency1Cost | number | The Currency1 cost of the Virtual Good
currency2Cost | number | The Currency2 cost of the Virtual Good
currency3Cost | number | The Currency3 cost of the Virtual Good
currency4Cost | number | The Currency4 cost of the Virtual Good
currency5Cost | number | The Currency5 cost of the Virtual Good
currency6Cost | number | The Currency6 cost of the Virtual Good
description | string | The description of the Virtual Good
googlePlayProductId | string | The google play productId of the item.
iosAppStoreProductId | string | The iOS AppStore productId of the item.
maxQuantity | number | The maximum number of the Virtual Good that can be owned at one time
name | string | The name of the Virtual Good
propertySet | JSON | The custom property set configured on the item.
psnStoreProductId | string | The PSN Store productId of the item.
shortCode | string | The short code of the Virtual Good
steamStoreProductId | string | The Steam Store productId of the item.
tags | string | The tags of the Virtual Good
type | string | The type of the virtual good, "VGOOD" or "CURRENCY"
w8StoreProductId | string | The Windows 8 productId of the item.


## Code Samples

<h3>C#</h3>
```cs
	using GameSparks.Api;
	using GameSparks.Api.Requests;
	using GameSparks.Api.Responses;
	...
	new ListVirtualGoodsRequest()
		.SetTags(tags)
		.Send((response) => {
		GSData scriptData = response.ScriptData; 
		GSEnumerable<var> virtualGoods = response.VirtualGoods; 
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
	    .createListVirtualGoodsRequest()
		.setTags(tags)
		.send(function(response:com.gamesparks.api.responses.ListVirtualGoodsResponse):void {
		var scriptData:ScriptData = response.getScriptData(); 
		var virtualGoods:Vector.<VirtualGood> = response.getVirtualGoods(); 
		});

```

### Objective-C
```objectivec
	#import "GS.h"
	#import "GSAPI.h"
	...
	GSListVirtualGoodsRequest* request = [[GSListVirtualGoodsRequest alloc] init];
	[request setTags:tags;
	[request setCallback:^ (GSListVirtualGoodsResponse* response) {
	NSDictionary* scriptData = [response getScriptData]; 
	NSArray* virtualGoods = [response getVirtualGoods]; 
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
	
	void ListVirtualGoodsRequest_Response(GS& gsInstance, const ListVirtualGoodsResponse& response) {
	GSData scriptData = response.getScriptData(); 
	gsstl:vector<Types::VirtualGood*> virtualGoods = response.getVirtualGoods(); 
	}
	......
	
	ListVirtualGoodsRequest request(gsInstance);
	request.SetTags(tags)
	request.Send(ListVirtualGoodsRequest_Response);
```

### Java
```java
import com.gamesparks.sdk.api.autogen.GSRequestBuilder.ListVirtualGoodsRequest;
import com.gamesparks.sdk.api.autogen.GSResponseBuilder.ListVirtualGoodsResponse;
import com.gamesparks.sdk.api.autogen.GSTypes.*;
import com.gamesparks.sdk.api.GSEventListener;

...
gs.getRequestBuilder().createListVirtualGoodsRequest()
	.setTags(tags)
	.send(new GSEventListener<ListVirtualGoodsResponse>() {
		@Override
		public void onEvent(ListVirtualGoodsResponse response) {
			GSData scriptData = response.getScriptData(); 
			List<VirtualGood> virtualGoods = response.getVirtualGoods(); 
		}
	});

```

### Cloud Code
```javascript

	var request = new SparkRequests.ListVirtualGoodsRequest();
	request.tags = ...;
	var response = request.Send();
	
var scriptData = response.scriptData; 
var virtualGoods = response.virtualGoods; 
```


