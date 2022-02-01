---
tags: state/seedling
---

# UE4 Collisions

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