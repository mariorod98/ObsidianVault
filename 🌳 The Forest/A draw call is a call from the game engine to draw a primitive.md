tags: #state/bud #on/graphics

# A draw call is a call from the game engine to draw a primitive
A draw call is a call that the game engine makes to the graphic engine to draw a primitive. It is composed of the last to steps of the [[A graphic pipeline is used to create a 2D representation from a 3D scene|graphic pipeline]].

Even though they are expensive, a draw call is executed for each geometry that must be painted in the screen. Therefore, one of the objectives of a graphics programmer is to reduce the number of draw calls per frame.

http://www.adriancourreges.com/blog/2015/11/02/gta-v-graphics-study-part-2/

---
Planted: 2022-01-14
Last tended: 2022-01-14
