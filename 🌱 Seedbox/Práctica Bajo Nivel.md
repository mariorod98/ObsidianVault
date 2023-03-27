Raytracing: Lanzas un rayo para cada pixel para ver dónde choca
Se hace raycasting contra un cilindro infinito que está centrado en z. Su equacion es `x^2 + y^2 = r^2`

Usar la ecuacion paramétrica de la recta

El efecto de movimiento se consigue cambiando las coordenadas de textura.

La ecuacion es:

```
x = aVx
y = aVy
z = aVz

donde V es un vector dirección
```

La incógnita de este vector es determinar cuál es el valor de `a`. Se obtiene sustituyendo la ecuación del cilindro en la ecuación de la recta.