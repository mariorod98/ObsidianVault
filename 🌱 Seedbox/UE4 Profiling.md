up::
tags:: #state/seedling

# UE4 Profiling

## Profiling GPU
Primero de profiling: checkear todas las luces y comprobar que su tipo es correcto. Las luces dinamicas son muy costosas.

En el editor, los tipos de pintado de Optimization Viewmode muestran información de las luces.
- Light Complexity. Muestra la complejidad de la luz, Si está rojo o verde maaal
- Lightmap Density. Tamaño de textura que ocupa cada objeto. Si se pinta azul, guay. Si se pinta verde, la resolución de textura es demasiado grande. Se puede cambiar seleccionando el objeto y cambiando la setting Overriden Light Map Res. Esta variable define la resolucion de la textura y debe ser potencia de 2.
- Shader Complexity. Lo que tarda el shader en dibujar cada elemento? Cuanto más verde mejor. ¿Qué da problemas? Transparencias. (F5 en tiempo real)

## Profiling CPU
1. Desactivar en ProjectSettings el check Frame Rate Smoothing.
2. Hacer la prueba en Play en Standalone y minimizando el editor.
3. Al lanzarlo, desactivar VSync mediante el comando `r.vsync 0` (para volver a ponerlo, usar el comando `r.vsync 1`).
4. El comando `Stat UnitGraph` se muestra una gráfica con el framerate del juego.
5. El comando `Stat UObjects` muestra cuánto consume cada elemento a nivel de código

## Guardar info de profiling en un fichero
`stat StartFile` comienza a guardar info en un fichero
`stat StopFile` pausa el guardado en fichero

## Profiling GPU

El archivo se guarda en Saved->Profiling. Este fichero se abre con el profiler de UE4. El profiler está en Developer Tools->Session Frontend
## References

---
Planted: 2023-01-17
Last tended: 2023-01-17
