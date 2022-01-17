---
tags: state/bud on/graphics
---

# What is a geometry pipeline?
The geometry pipeline corresponds to the geometry stage of the [[A graphic pipeline is used to create a 2D representation from a 3D scene|graphic pipeline]]. It is responsible for the majority of the operation with polygons and their vertices. The objective of this pipeline is to **transform the vertices of the primitives from model space to clipping space**. It has three steps:
1. The first step is to **transform vertices in model space into world space**. This means that the vertices must be put on the scene we want to draw. Each primitive in the scene will have an associated [[world transform]] that indicates the position, rotation and scale of the primitive in the world. To transform the vertices from model space into world space, the [[world transform]] must be applied to all the vertices of the primitive.
2. The [[Virtual Camera]] is a special object in the scene that determines what part of the scene will be shown. It has its own transform, so it is located somewhere in the world. The next step is to move the world so that the camera is at the origin and facing to Z axis. In other words, the pipeline must **transform vertices in world space to view space**. To achieve this, we must apply the [[view matrix]] transformation to all the vertices in the scene. 
3. Finally, all the vertices inside the view space must be confined into the [[clipping space]]. To do this, the pipeline has to **transform vertices in view space to clipping space** applying the [[projection matrix]].

  
![[geometry_pipeline.png]]

---
Planted: 2022-01-16
Last tended: 2022-01-16