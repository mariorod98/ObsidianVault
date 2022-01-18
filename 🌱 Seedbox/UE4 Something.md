---
tags: state/seedling
---

# UE4 Something
CoreMinimal.h - clases minimas del motor
Class.generated.h - clase generada automaticamente por el motor para conectar la clase en codigo a su representacion en bp.

UCLASS y GENERATED_BODY son macros que inyectan código como elementos del recolector de basura o para la representación en bp.

Si no vamos a usar el tick, es mejor borrarlo.

En el constructor vamos a inciializar la memoria de los componentes y especificar la jerarquia de estos.

El constructor es delicado. Cuando lo toquemos, hay que:
1. Cerrarlo todo.
2. Borrar las dlls.
3. Modificar el constructor.
4. Abrir el proyecto otra vez

Al hacer override, SIEMPRE hay que comprobar si hay que llamar a super o no. Los metodos BeginPlay y Tick SIEMPRE tienen que tener llamada a super.

- [ ] Mirar modos de compilacion de visual studio para ue4
- [ ] seguir tutorial para configurar el visual studio con ue4

---
Planted: 2022-01-18
Last tended: 2022-01-18