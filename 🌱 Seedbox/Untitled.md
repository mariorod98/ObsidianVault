Lvalue, cualquier cosa que se pueda poner a la izquierda de una asignacion

Rvalue, cualquier cosa que NO se pueda poner a la izquierda de una asignacion

```cpp
int a;

a = 3; // a = lvalue, 3 = rvalue
```

El constructor de copia admite un l-value
El constructor move admite un r-value