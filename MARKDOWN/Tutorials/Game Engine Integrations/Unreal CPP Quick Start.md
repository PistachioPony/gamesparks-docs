---
nav_sort: 2
src: /Tutorials/Game Engine Integrations/Unreal CPP Quick Start.md
---

# Unreal CPP QuickStart

## Initialization

### GameMode.h

Include the following headers:

```
#include "GameSparks/GS.h"
#include "GameSparks/IGSPlatform.h"
#include "GameSparks/generated/GSRequests.h"
#include "GameSparks/generated/GSResponses.h"
#include "GameSparks/generated/GSMessages.h"
#include "GameSparks/Private/GameSparksComponent.h"

//Add these namespaces
using namespace GameSparks::Core;
using namespace GameSparks::Api::Messages;
using namespace GameSparks::Api::Responses;
using namespace GameSparks::Api::Requests;

```

Create a public variable for the GameSparks component:

```
UGameSparksComponent* GameSparksComp;

```

Add your GameMode's constructor and begin play. With it a UFUNCTION with a bool parameter to handle the *OnGameSparksAvailableDelegate* invocation:

```
//Constructor
	AMyGameMode();

	//BeginPlay
	virtual void BeginPlay() override;

	//Function used to determine what happens if GameSparks connects or fails to (Needs to be UFUNCTION)
	UFUNCTION()
	void bindFunc(bool available);

```

### GameMode.CPP

In your GameMode's constructor initialize the GameSparks Component:

```
AMyGameMode::AMyGameMode() {

	GameSparksComp = CreateDefaultSubobject<UGameSparksComponent>(TEXT("GSparkComp"));

}
```

In your GameMode's BeginPlay function add your handler function to the *OnGameSparksAvailableDelegate* invocation list then call the Connect function from your GameSparks Component:

```
void AMyGameMode::BeginPlay() {

	Super::BeginPlay();

	GameSparksComp->OnGameSparksAvailableDelegate.AddDynamic(this, &AMyGameMode::bindFunc);


	GameSparksComp->Connect("297447wFen65", "sB5CC6ATGd9oa7pUiDCfYofEhalrudSb");

}
```

Finally just add logic to your handler function to execute code when GameSparks becomes available:

```
void AMyGameMode::bindFunc(bool available) {

		GEngine->AddOnScreenDebugMessage(-1, 15.0f, FColor::Red, available? "True":"False");
}
```

Refer to the [CPP quick start guide](/Tutorials/Game Engine Integrations/CPP Quick Start.md) for simple C++ GameSparks functions.
