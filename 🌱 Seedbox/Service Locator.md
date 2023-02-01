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
#include <vector>
#include <algorithm>
#include <typeid>

class IServiceA {};
class IServiceB {};
class IServiceC {};

struct ServiceHolder {
	size_t type;
	void* ptr;
	
	// Sirve para implementar todos los operadores lógicos a la vez
	// Devuelve negativo si es menor, 0 si es igual y positivo si es mayor
	int operator<=>(const ServiceHolder& other) {
		return static_cast<int>(type - other.type);
	}
};

class ServiceLocator {
 public:
	template<typename T> T& get() {
		auto result = std::lower_bound(service_vector.begin(), service_vector.end(), typeid(T).hash_code());
		if(result == service_vector.end()) {
		
		}
		else {
		
		}
	}
	
	template<typename T> add(T* service) {
		service_list_.emplace_back({typeid(T).hash_code(), service});
		std::sort(service_vector.begin(), service_vector.end());
	}
 private:
 // Cuando el número de objetos es bajo (<=50), un vector es mucho más eficiente que otras estructuras (como un map) ya que se puede cargar todo el bloque de memoria del vector directamente a la caché. En las otras estructuras, los elementos pueden estar muy espaciados en memoria.
	std::vector<ServiceHolder> service_vector;
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