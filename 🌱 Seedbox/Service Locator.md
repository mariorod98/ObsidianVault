up::
tags:: #state/seedling

# Service Locator
Una clase con un montón de punteros a interfaces, esta clase se pasa como "contexto" a los objetos que la necesiten.

Tips:
- Que no tenga punteros a servicios específicos, sino a interfaces genéricas. Ya que va a ser una clase muy modificada durante la vida del código.
- Templatizar el ServiceLocator

**Implementación sencilla**
```cpp 
class IServiceA {};
class IServiceB {};
class IServiceC {};

class ServiceLocator {
 public:
	 IServiceA& getA() {return *a;}
	 IServiceB& getB() {return *b;}
	 IServiceC& getC() {return *c;}

 private:
	IServiceA* a = nullptr;
	IServiceB* b = nullptr;
	IServiceC* c = nullptr;
};

class ClaseUsuario {
 public:
	 ClaseUsuario(ServiceLocator& sl) : sl{sl} {sl.a.doSomething();}
private:
	ServiceLocator& sl;
};

int main() {
	ServiceLocator sl;
	ClaseUsuario cu{sl};
}
```

**Implementación con templates**
```cpp 
class IServiceA {};
class IServiceB {};
class IServiceC {};


class ServiceLocator {
 public:
	template<typename T> T& get();
	template<typename T> Add(T* service);
 private:
	IServiceA* a = nullptr;
	IServiceB* b = nullptr;
	IServiceC* c = nullptr;
};

class ClaseUsuario {
 public:
	 ClaseUsuario(ServiceLocator& sl) : sl{sl} {sl.a.doSomething();}
private:
	ServiceLocator& sl;
};

int main() {
	ServiceLocator sl;
	ClaseUsuario cu{sl};
}
```
## References

---
Planted: 2023-02-01
Last tended: 2023-02-01