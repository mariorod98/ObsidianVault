Formatos para representar mallas.

- Sucesion de triangulos
    - v0 v1 v2 v0 v2 v3 v2 v3 v4
    - t0 (v0, v1, v2) t1 (v0, v2, v3) t2(v2, v3, v4)
    - Repite vértices, si se tiene que aplicar una transformacion al vertice, se debe repetir para cada triangulo
- Triangle strips: cada vertice crea un triangulo nuevo
    - v0, v1, v2, v3, v4
    - t0 (v0, v1, v2) t1(v2, v1, v3) t2(v2, v4, v3)
    - Deben ser mallas muy regulares
- Formato de tapas (GL_FAN): el primer vertice indica el centro de la tapa, el resto de vertices se utilizan para crear triangulos a partir del centro
    - v0, v1, v2, v3, v4
    - t0 (v0, v1, v2) t1 (v0, v2, v3) t2 (v0, v3, v4)
- Formato vértices + indices: a cada vertice le das un indice (int). Los triangulos se forman con esos indices. Esta representacion es similar a la primera pero no se repiten los indices.
    - v0 (0), v1 (1), v2 (2), v3 (3)
    - t0 (0, 1, 2) t1 (2, 1, 3)

![[triangle_strip.png]]

![[triangle_fan.png]]

00000000 00000000 00000000 11111111 
11111111 00000000 00000000 00000000 