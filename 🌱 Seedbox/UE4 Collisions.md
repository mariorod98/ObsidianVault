---
tags: state/seedling
---

# UE4 Collisions
UE4 handles collisions at a [[A component is an Object that actors can attach to themselves|Component]] level. All the components derived from __UPrimitiveComponent__ have collision properties (UBoxComponent, UStaticMeshComponent, USkeletalMeshComponent, etc).

The collision primitive can be set in the inspector of the component and the collision parameters appear in the Details inspector in the section _Collision_.

## Collision properties
## Collision responses
In UE4, collisions and ray casting are handled through the _Collision Responses_ and _Trace Responses_. There are three types of responses an object can have:
- Block is used for objects that will block movement of incoming objects, they will _collide_. This response generates a Hit event.
- Overlap is used for objects that can be penetrated by incoming objects. This response generates a BeginOverlap and EndOverlap events.
- Ignore.
## Collision presets
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

Collision enabled:
- No collision: No detecta ni raycast, ni overlap ni hit.
- Query only: solo raycast y overlap, no hit.
- Physics only: solo hit
- Collision enabled: raycast, overlap y hit.

FActorBeginOverlap
FActorEndOverlap

Object type:
---
Planted: 2022-01-31
Last tended: 2022-02-02