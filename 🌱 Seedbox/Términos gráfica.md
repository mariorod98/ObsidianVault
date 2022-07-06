up:
tags: #state/seedling 

# Términos gráfica
**Backface culling** es una técnica para evitar pintar las caras opuestas a las que se ven en cámara. Pues si una cara se ve en cámara, su opuesta nunca se verá.

Cuando el polígono está proyectado, se calcula si el polígono está en clockwise o anticlockwise order. El motor tendrá fija una de las orientaciones como la de frente (normalmente anticlockwise). Si el polígono está en esa orientación, está de frente. Si está en la otra orientación, esta de espalda.

En 2D se utiliza el cross product entre dos vectores del polígono y se observa su signo. 
En 3D se determina si el plano está mirando hacia el interior del objeto o hacia el exterior.

Además del backface culling, existe el **frontface culling** (No pinta la cara frontal) y el **double sided** (pinta ambas caras).

**Fillrate**


**Alpha Blending** es una técnica que mezcla dos píxeles mediante un LERP y un valor alpha.

---
Planted: 2022-01-19
Last tended: 2022-01-19