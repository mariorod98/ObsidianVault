RPC server notifies the copied actor in the server

to check if the actor is in a client (instead of a server), use IsLocallyConnected
To check if an actor is in the server, use HasAuthority

RPC client notifies the owner of an actor in their client

RPC multicast notifies all clients that have the actor