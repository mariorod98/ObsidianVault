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
};

bool operator<=>(const ServiceHolder& a, const Serviceholder& b) {

}

class ServiceLocator {
 public:
	template<typename T> T& get();
	template<typename T> Add(T* service) {
		service_list_.emplace_back({typeid(T).hash_coce(), service});
		void* ptr
	}
 private:
	std::vector<ServiceHolder> service_vector_;
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