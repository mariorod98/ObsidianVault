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
When Replication is enabled on an AActor, its variables may be replicated. To do so in Blueprint, select the variable and set the flag *Replicated* to true. 

In C++, there are two ways to replicate:

- Using the [[UE4 Macros|UPROPERTY]] *Replicated*. And implementing in the cpp file the method *GetLifeTimeReplicatedProps*.

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

- Using the [[UE4 Macros|UPROPERTY]] *ReplicatedUsing=* followed by the name of the method used to replicate the variable. This method MUST be UFUNCTION.

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
```
## References

---
Planted: 2023-02-14
Last tended: 2023-02-14