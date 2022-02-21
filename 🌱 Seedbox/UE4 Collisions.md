---
tags: state/seedling on/ue4
---

# UE4 Collisions
UE4 handles collisions at a [[A component is an Object that actors can attach to themselves|Component]] level. All the components derived from __UPrimitiveComponent__ have collision properties (UBoxComponent, UStaticMeshComponent, USkeletalMeshComponent, etc).

The collision primitive can be set in the inspector of the component and the collision parameters appear in the Details inspector in the section _Collision_.

## Collision properties
### Collision responses
In UE4, collisions and ray casting are handled through the _Collision Responses_ and _Trace Responses_. These responses define how a physics body should interact with all of the objects and traces. The event dispatched by the response (hit or overlap) depends on two parameters: the type of response generated and the type of object that generates the response.

There are three types of responses an object can have:
- Block is used for objects that will block movement of incoming objects, they will _collide_. This response generates a Hit event.
- Overlap is used for objects that can be penetrated by incoming objects. This response generates a BeginOverlap and EndOverlap events.
- Ignore the interaction.

When two Physic Objects collide, one of these responses will be generated. If both objects have different responses, the most restrictive one will be taken into account. The restriction order is: Ignore->Overlap->Block.

For example, if a object with Block responses collides with an object with Overlap responses, then an Overlap response will be generated. Likewise, an interaction with an Overlap or Block object with an Ignore object will never generate a response.

The type of traces and objects that generate a response are:
- Trace Types.
    - Visibility. General visibility testing channel.
    - Camera. Usually used when tracing from the camera to something.
- [[Object Types]].
    - WorldStatic.
    - WorldDynamic.
    - Pawn. 
    - Vehicle.
    - Destructible.
### Collision enabled
This option determines the types of collision that this actor has enabled. It is used to optimize how many types of collision the engine must perform on the actor. There are four different options:
- No collision: Doesn't detect any collisions. It is the most efficient.
- Query only: Only detects raycast, sweep and overlap. Does not detect hit events.
- Physics only: Only detects hit events.
- Collision enabled: raycast, overlap y hit.
### Collision presets
The collision presets are a set of predefined responses that can be selected for a specific actor or class. There are several basic collision presets, but the user can specify custom presets in the Project Settings. The default collision presets are:

| Preset | Description |
|---|---|
|Default|Use the settings that were applied to the Static Mesh in the Static Mesh Editor.|
|NoCollision|No collision.|
|BlockAll|WorldStatic object that blocks all actors by default.|
|OverlapAll|WorldStatic object that overlaps all actors by default.|
|BlockAllDynamic|WorldDynamic object that blocks all actors by default.|
|OverlapAllDynamic|WorldDynamic object that overlaps all actors by default.|
|IgnoreOnlyPawn|WorldDynamic object that ignores Pawn and Vehicle.|
|OverlapOnlyPawn|WorldDynamic object that overlaps Pawn, Camera and Vehicle.|
|Pawn|Pawn object. Can be used for capsule of any playable character or AI.|
|Spectator|Pawn object that ignores all other actors except static actors.|
|CharacterMesh|Pawn object that is used for Character Mesh.|
|PhysicsActor|Simulating actors.|
|Destructible|Destructible actors.|
|InvisibleWall|WorldStatic object that is invisible.|
|InvisibleWallDynamic|WorldDynamic object that is invisible.|
|Trigger|WorldDynamic object that is used for trigger.|
|Ragdoll|Simulating Skeletal Mesh Component.|
|Vehicle|Vehicle object that blocks Vehicle, WorldStatic and WorldDynamic objects.|
|UI|WorldStatic object that overlaps all actors by default.|



Cualquier componente que hereda de primitive tiene un apartado para las colisiones.



FActorBeginOverlap
FActorEndOverlap

---
Planted: 2022-01-31
Last tended: 2022-02-07