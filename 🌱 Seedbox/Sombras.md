up::
tags:: #state/seedling

# Sombras

Desde la posicion y perspectiva de la luz, pintamos el z buffer para ver qué objetos ve la luz. Desconectar los read & write buffers.

Desde el punto de vista del usuario, cogemos el fragmento y sacamos sus coordenadas en el mundo. Si cogemos esa coordenada y la multiplicamos por la transform de la luz, obtenemos esa coordenada desde el punto de vista de la luz.

Comparando el z buffer con la z de esa ultima posicion, podemos ver si es iluminado o no.

## References

---
Planted: 2023-03-07
Last tended: 2023-03-07