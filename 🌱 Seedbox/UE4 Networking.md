up:: [[⚙️Unreal Engine 4]]
tags:: #state/seedling #on/ue4/multiplayer

# UE4 Networking

Unreal Engine 4 uses a standard **Server-Client architecture** where the Server is authoritative and all data must be send from Client to Server first. Then, the Server validates the data and reacts depending on your code.

The Server can be eithe *dedicated* or *listen*.
- A **dedicated Server** is a standalone Server that does NOT require a Client. They can be compiled for Windows and Linux and can be run on Virtual Servers that Players can connect to via a fixed IP Address. They don't have visual parts, so they don't need a UI nor an APlayerController.
- A **listen Server** is a Server that is also a Client. If the Client disconnects, the Server will shut down. Due to being a Client, the Client-Server needs a UI and an APlayerController

## UE4 Framework when networking
The UE4 framework can ve split into different sections depending on where the object resides:
- **Server Only**. The object only exists on the Server.
- **Server & Clients**. These objects exists on the Server and on all Clients.
- **Server & Owning Client**. These objects only exist on the Server and the owning Client (the player who owns the Actor).
- **Owning Client Only**. These objects only exist on the owning Client.

![[ue4_networking_architecture.png]]

### Game Mode
The AGameMode is used to define the rules of the game. **It is only available on the Server**. ==Any Client that tries to get the AGameMode will receive a nullptr==.

Some useful methods and events in the GameMode in multiplayer games are:
- *OnPostLogin*. An event that is called whenever a Player joins the Game.
- *ReadyToStartMatch*.
- *ReadyToEndMatch*.
*- OnRestartPlayer.*
- *OnLogout*.
- *ChoosePlayerStart*.
- *FindPlayerStart*.

### Game State
The AGameState is probably the most important class for shared information between Server and Clients. **It is used to keep track of the current State of the Game**. For example, a list of connected players (APlayerState).

==The AGameState is replicated to all Clients, so everyone can access it.==

### Player State
The APlayerState is the most important class for a specific Player. **It is meant to hold current information about the Player**. ==It is replicated to everyone and can be used to retreive and display data on other Clients==.

It is also used to make sure that the data stays consistent during Level changes and unexpected connection issues.

### Pawn
The class APawn is the actor that the player controls. **The pawn is mostly replicated to all Clients**.

### Player Controller
The APlayerController is the first class that the Client actually owns, with a copy existing on the Server. **Every Client only knows about its own APlayerController**. 

### HUD
The class AHUD is only avaliable on each Client and can be accessed through the PlayerController. 

### Widgets
Widgets are only available locally on Client. They are NOT replicated and you always need a separated, replicated class to perform the replicated action.

## Replication
Replication is the act of the Server passing information to the Clients. This can be limited to specific entities and groups.

In Blueprint, replication is activated by setting the *Replicates* flag in to true in the AActor whose information we want to replicate. In C++, it is activated by setting the bool bReplicates to true in the constructor.

==When an AActor is set to replicate, it will ONLY be spawned and replicated on all Clients if it is spawned by the Server. If a Client spawns the Actor, it will ONLY exist on the owning Client.==

### Variable Replication
When Replication is enabled on an AActor, its variables may be replicated. 
To do so in Blueprint, select the variable and set the flag *Replicated* to true. 

In C++, the replication is done using the [[UE4 Macros|UPROPERTY]] *Replicated*. And implementing in the cpp file the method *GetLifeTimeReplicatedProps*.

```cpp
// AMyActor.h
UPROPERTY(Replicated)
float health_;

// AMyActor.cpp
void AMyActor::GetLifetimeReplicatedProps( TArray< FLifetimeProperty > & OutLifetimeProps ) const
{
	// Replication without conditions
    DOREPLIFETIME( AMyActor, health_);

	// Replication with conditions
	DOREPLIFETIME(AMyActor, health_, COND_OwnerOnly)
}
```

The Replication conditions are:
![[ue4_networking_rep_cond.png]]

There is another way to Replicate a variable: *RepNotify*. This makes use of a function that will be called on **all instances** when receiven the updated value.

With RepNotify, ==you can call logic that needs to be called AFTER the value has been replicated==.

In Blueprint this function will be automatically created when selectin RepNotify as the Replication method.

In C++ it is implemented using the [[UE4 Macros|UPROPERTY]] *ReplicatedUsing=* followed by the name of the method used to replicate the variable. This method MUST be UFUNCTION. The method *GetLifeTimeReplicatedProps* must also be implemented.

```cpp
// AMyActor.h
UPROPERTY(ReplicatedUsing=OnRep_Health)
float health_;

UFUNCTION()
void OnRep_Health();

// AMyActor.cpp
void AMyActor::OnRep_Health() {
	if(health_ < 0.0f) {
		PlayDeathAnimation();
	}
}

void AMyActor::GetLifetimeReplicatedProps( TArray< FLifetimeProperty > & OutLifetimeProps ) const
{
	// Replication without conditions
    DOREPLIFETIME( AMyActor, health_);

	// Replication with conditions
	DOREPLIFETIME(AMyActor, health_, COND_OwnerOnly)
}
```

When the variable *health_* is successfully replicated, the function *OnRep_Health* is called.

## Remote Procedure Calls (RPCs)
RPCs are methods called from one instance of the AActor to another instance of the AActor. They can be used to call functions from Client to Server, Server to Client or Server to a specific group of Clients.

==RPCs do not return value. To return something, you need to use a second RPC==.

An RPC can be classified as:
- **Run on server**. It is meant to be executed on the server Instance of the AActor.
- **Run on owning Client**. It is meant to be executed on the Owner of the AActor.
- **NetMulticast**. It is meant to be executed on all the instances of the AActor.

For a RPC to work, it must follow these **rules**:
1. They must be called from AActors.
2. The AActor must be replicated.
3. If the RPC is from Server to Client, only the owner will execute the function.
4. If the RPC is from Client to Server, only the owner can launch the RPC.
5. Multicast RPCs are an exeception:
	- If they are called from the server, the Server will execute them locally and on all the currently connected Clients.
	- If they are called from Clientes, they will only execute locally.
	- A Multicast RPC will not replicate more than twice in a given period (AActor's network update period).

Given these rules, and depending on the ownership of the AActor, the following tables determine the behaviour of the RPC:

**RPC invoked form the Server**

|  Ownership  | Not replicated | NetMulticast           | Server | Client        |
|:-----------:| -------------- | ---------------------- | ------ | ------------- |
| **Client**  | Server         | Server and all Clients | Server | Owning client |
| **Server**  | Server         | Server and all Clients | Server | Server        |
| **Unowned** | Server         | Server and all Clients | Server | Server        |

**RPC invoked form a Client**

|     Ownership     | Not replicated  | NetMulticast    | Server | Client          | 
|:-----------------:| --------------- | --------------- | ------ | --------------- |
| **Owning Client** | Invoking Client | Invoking Client | Server | Invoking Client |
| **Other Client**  | Invoking Client | Invoking Client | Server | Invoking Client |
|    **Server**     | Invoking Client | Invoking Client | Server | Invoking Client |
|    **Unowned**    | Invoking Client | Invoking Client | Server | Invoking Client |


### RPCs in Blueprints
To create a RPC in Blueprint you just have to create a Custom Event and set its *Replicates* property to the type of RPC you want.

The *Reliable* property can be checked to mark the RPC as *important* and make sure it will 99.99% be executed. Do not mark every RPC as *Reliable*.

### RPCs in C++
To create an RPC in C++, you need to create a method with the UFUNCTION() macro specifying:
- The type or RPC: Server, Client, NetMulticast.
- Whether it is reliable or unreliable.
- Whether the RPC must be validated or not (with the parameter *WithValidation*).

```cpp
// Server RPC that is unreliable and has validation
UFUNCTION(Server, unreliable, WithValidation)
void Server_PlaceBomb();

// Client RPC that is reliable and does not have validation
UFUNCTION(Client, reliable)
void ReliableClient_PlaceBomb();

// Multicst RPC that is unreliable and has validation
UFUNCTION(NetMulticast, unreliable, WithValidation)
void Multicast_PlaceBomb();
```

Then you have to implement the method and, if it has the parameter *WithValidation*, you have to implement the validation method.

```cpp
// AMyActor.h
UFUNCTION(Server, unreliable, WithValidation)
void Server_PlaceBomb(AActor* bomb);

// AMyActor.cpp
void AMyActor::Server_PlaceBomb_Implementation(AActor* bomb) {
	bomb.BOOM();
}

bool AMyActor::Server_PlaceBomb_Validate(AActor* bomb) {
	return bomb != nullptr;
}
```

### Validation
The validation function detects if any parameter of the RPC is bad and, in that case, notifies the system to disconnect the Client/Server who initiated the RPC call. **Validation is required for every ServerRPCFunction** to encourage secure Server RPC functions.

### Ownership
One of the most important concepts to understand RPCs is the concept of ownership. **Both Server or Clients can own an AActor**. When calling an RPC, it is important to know who is the owner of the AActor because ==if a Client calls a Server RPC on an AActor that it does NOT own, the RPC is dropped==.

The tables above show the action that will happen depending on the ownership of the AActor.

**The ownership is inherited between AActors**. If an APlayerController possesses an APawn and the APlayerController is owned by a Client, then the Client owns both the APawn and APlayerController.

One of the main problems with this architecture is that a Client cannot call Server RPCs of almost any object in the Scene. To work around this, we can use the PlayerController, that is owned by the Client and replicated to the Server, to call a Server RPC from the Client to the Server. This RPC can then call perform the action we desire in the Server.

For example, if the player wants to open a door. Instead of trying to open the door AActor in the Client side, we send a Server RPC to the APlayerController in the Server to open that door. 

## Relevancy
To avoid collapsing the network with useless information, Unreal uses the *Relevancy* of AActors to determine if their information should be shared through the network or not. 

The following rules are used to determine the **relevant set of Actors** for a Client.
1. If the AActor is *bAlwaysRelevant*, is owned by the APawn or the APlayer controller, is the Pawn or the Pawn is the instigator of some action (like noise or damage), it is **relevant**.
2. If the AActor is *bNetUserOwnerRelevancy* and has an Owner, **use the Owner's relevancy.**
3. If the AActor is *bOnlyRelevantToOwner* and does not pass the first check, it is **not relevant**.
4. If the Actor is attached to the Skeleton of another AActor, then **its relevancy is determined by the relevancy of its base**.
5. If the AActor is hidden (*bHidden == true*) and the root component does not collide, then the actor is **not relevant**.
6. If AGameNetworkManager is set to use distance based relevancy, **the AActor is relevant if it is closer than the net cull distance**.

## Priorization
Unreal uses a **load-balancing technique** to prioritize all AActors. It gives to each AActor a percentage of bandwith depending on the priority of the AActor.

Every AActor has the default priority of 1.0. If you set an AActor's *NetPriority* to 2.0 then it will update twice as frequently as the AActors with a *NetPriority* of 1.0.

## Actor Role and RemoteRole
These two properties determine:
- Who has the **Authority** over the AActor.
- Whether the AActor is replicated or not.
- The Mode of the replication.

To check who has the **Authority** of an AActor, we have to check that the *Role* property is set to *ROLE_Authority*. If it is, then this instance of the Engine is in charge of this AActor.

## References

---
Planted: 2023-02-14
Last tended: 2023-02-14