up: [[🌈 Graphics Programming]]
tags: #state/bud #on/graphics


# What is a graphic pipeline?
A graphic pipeline is a sequence of steps used to create a 2D raster representation of a [[3D scene]]. The pipeline's input includes the vertices, materials and cameras of the scene and it produces an array of RGB pixels that will be shown in a screen.

The GP process is as follows:
1. Apply transformations to the vertices.
2. [[What is rasterization | Rasterize]] the geometric primitives of the scene.
3. Obtain the RGB value of each pixel.

# What are the stages of a graphic pipeline?
The graphic pipeline has three main stages: Application, Geometry and Rasterization. The last two stages are involved in [[A draw call is a call from the game engine to draw a primitive | draw calls]].

## Application
- It is done in the CPU.
- All the operations that change the scene are processed here. Such as animations, physics, user input, collision detection, etc.
- After all the modifications are applied to the scene, it is sent to the GPU.
## [[The geometry pipeline transform vertices form model space to clipping space|Geometry]]
- It is done in the GPU.
- This step is responsible for applying all the geometrical transformations to the objects in order to create the scene. 
- To achieve this, it must calculate such things as lighting, projection, and clipping.
- [[Vertex shaders]] work in this stage.
## Rasterization
- It is done in the GPU.
- It is the responsible for calculating the color of each pixel in the screen.
- Before calculating the color, it must [[What is rasterization | rasterize]] the primitives in order to obtain the pixels that are affected by that primitive.
- Each pixel is treated independently.
- In this stage, the user can use [[pixel shaders]] (also called fragment shaders) to modify the pixel color.

---
Planted: 2022-01-16
Last tended: 2022-01-16