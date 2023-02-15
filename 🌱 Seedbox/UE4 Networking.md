up:: [[⚙️Unreal Engine 4]]
tags:: #state/seedling #on/ue4/multiplayer

# UE4 Networking

Unreal Engine 4 uses a standard **Server-Client architecture** where the server is authoritative and all data must be send from Client to Server first. Then, the server validates the data and reacts depending on your code.

## UE4 Framework when networking
The UE4 framework can ve split into different sections depending on where the object resides:
- **Server Only**. The object only exists on the server.
- **Server & Clients**. These objects exists on the server and on all clients.
- **Server & Owning Client**. These objects only exist on the server and the owning client (the player who owns the Actor).
- **Owning Client Only**. These objects only exist on the owning client.
![[ue4_networking_architecture.png]]

### Game Mode
The AGameMode is used to define the rules of the game. **It is only available on the Server**. ==Any client that tries to get the AGameMode will receive a nullptr==.

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

==The AGameState is replicated to all clients, so everyone can access it.==

### Player State
The APlayerState is the most important class for a specific Player. **It is meant to hold current information about the Player**. ==It is replicated to everyone and can be used to retreive and display data on other Clients==.

It is also used to make sure that the data stays consistent during Level changes and unexpected connection issues.

### Pawn
The class APawn is the actor that the player controls. **The pawn is mostly replicated to all clients**.
## References

---
Planted: 2023-02-14
Last tended: 2023-02-14