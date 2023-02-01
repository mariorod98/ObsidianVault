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

struct ServiceHolder {
	size_t type;
	void* ptr;
	
	// Sirve para implementar todos los operadores lógicos a la vez
	// Devuelve negativo si es menor, 0 si es igual y positivo si es mayor
	int operator<=>(const ServiceHolder& other) {
		return type - other.type;
	}
};

class ServiceLocator {
 public:
	template<typename T> T& get() {
		// la binary search es más óptima para vectores con pocos elementos (max 50) ya que los elementos se pueden cargar en la caché en un único paso y el procesador puede hacer la búsqueda rápidamente. Si hay muchos más elementos, un map/set es una mejor opción a un vector.
		std::binary_search(service_vector.begin(), service_vector.end(), typeid(T).hash_code());
	}
	
	template<typename T> add(T* service) {
		service_list_.emplace_back({typeid(T).hash_code(), service});
		std::sort(service_vector.begin(), service_vector.end());
	}
 private:
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