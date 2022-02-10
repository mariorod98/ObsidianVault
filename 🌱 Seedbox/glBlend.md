glBlendFunc(config triangulo [alpha], config fondo [beta])

Blend = alpha * A + beta * B
A: pixel triangulo
B: pixel fondo

glBlend(GL_ONE, GL_ONE) :  blending aditivo - suma los dos colores
glBlend(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA): transparencia de triangulo

buscar dithering y dithering types

mirar renderdoc