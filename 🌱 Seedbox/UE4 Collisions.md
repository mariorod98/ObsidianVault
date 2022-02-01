---
tags: state/seedling
---

# UE4 Collisions
UE4 handles collisions at a [[A component is an Object that actors can attach to themselves|Component]] level. All the components derived from __UPrimitiveComponent__ have collision properties (UBoxComponent, UStaticMeshComponent, USkeletalMeshComponent, etc).

The collision primitive can be set in the inspector of the component and the collision parameters appear in the Details inspector in the section _Collision_.

## Collision properties


In UE4, collisions and ray casting are handled through the _Collision Responses_ and _Trace Responses_.

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
Last tended: 2022-01-31