Raytracing: Lanzas un rayo para cada pixel para ver dónde choca
Se hace raycasting contra un cilindro infinito que está centrado en z. Su equacion es `x^2 + y^2 = r^2`

Usar la ecuación paramétrica de la recta

El efecto de movimiento se consigue cambiando las coordenadas de textura.

La ecuación es:

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
		wrap_text(&u, &v, Xcut, Ycut, Zcut)
```


- [x] Hacer el ray de la cámara al pixel.
- [x] Calcular alfa (el parámetro de la ecuación para obtener el punto de corte del rayo con el cilindro).
- [x] Obtener el punto de corte.
- [x] Calcular la iluminación.
- [x] Pintar una textura.
- [x] Hacer que la textura se mueva en z.
- [x] Girar la cámara.
-
## Optimización
Realizar menos cortes e interpolar la UV y light entre los valores calculados.

Nodo de interseccion
struct {float u,v,l}
struct[] = new[(w / 16 + 1) * (h / 16 + 1)]

Bucle de calculo intersecciones
for y + 16
	for x + 16
	
Bucle de dibujado
for y += 16
	for x += 16
		for sy++
			for sx++

Optimización extra:
en vez de girar los rayos, girar el frustum