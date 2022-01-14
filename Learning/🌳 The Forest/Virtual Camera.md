---
tags: state/bud on/graphics
---

# Virtual Camera
A virtual camera is a special object in a scene that specifies the space of the scene that will be represented in the image. **It determines the visible area of a scene**.
It is composed of:
- A [[transform matrix]] that determines its position, rotation and scale in the world.
- A [[frustum]] that determines the area of the world that will be painted in the final image.


