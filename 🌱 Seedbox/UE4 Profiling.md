up::
tags:: #state/seedling

# UE4 Profiling

# Luces
Primero de profiling: checkear todas las luces y comprobar que su tipo es correcto. Las luces dinamicas son muy costosas.

En el editor, los tipos de pintado de Optimization Viewmode muestran información de las luces.
- Light Complexity. Muestra la complejidad de la luz, Si está rojo o verde maaal
- Lightmap Density. Tamaño de textura que ocupa cada objeto. Si se pinta azul, guay. Si se pinta verde, la resolución de textura es demasiado grande. Se puede cambiar seleccionando el objeto y cambiando la setting Overriden Light Map Res. Esta variable define la resolucion de la textura y debe ser potencia de 2.
## References

---
Planted: 2023-01-17
Last tended: 2023-01-17
