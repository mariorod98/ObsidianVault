# En el entity (UE4)
**Pros**
- No hay que acceder al TransformComponent para acceder a su padre/hijos
- Es mas facil matar a los hijos cuando matas a la entity
**Contras**
- Para calcular la transform acumulada, tienes que acceder a la entity desde el componente
# En el transform (Unity)
**Pros**
- Es mas facil calcular la transform acumulada
**Contras**
- Es mas dificil matar a los hijos cuando matas a la entity
- Todas las entities tienen que tener transform component