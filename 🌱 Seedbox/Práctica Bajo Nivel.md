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

La incógnita de este vector es determinar cuál es el valor de `a` (alpha). Se obtiene sustituyendo la ecuación del cilindro en la ecuación de la recta.


Bucle de raytracing

```
for(y..)
	for(x...)
		// a partir de x e y, obtener el vector
		getVect(&v, x, y);
		rot3D(&v)
		alpha = raycast(&v)
		light = calculate_light(z_cut)
		wrap_text(&v, )
```