---
tags: state/bud on/ue4/interface
---

# UE4 Interface
C++ does not support interfaces. In order to implement them, UE4 uses a special class, **UInterface**, that simulates an interface. Custom interfaces in UE4 are composed of two distinct classes: a *UClassName* that inherits from UInterface, and a *IClassName* that doesn't inherit from anything. 

The first class is used by UE4 for [[the reflection system]]. It must be preceded by the [[UE4 Macros|UINTERFACE macro]]. This macro may have the following specifiers:
- BlueprintType. Exposes this class as a type that can be used for variables in Blueprints.
- MinimalAPI. Indicates that the class can be casted to but the methods cannot be called.

The second class is the one that will be inherited by other classes and where we will define the interface's methods.

### Inheritance
To inherit an interface, the class must inherit from the *I-prefixed* class:
```
UCLASS(Blueprintable, Category="MyGame")
class ATrap : public AActor, public IPickable
{
    GENERATED_BODY()

public:
    /** Add interface function overrides here. */
}
```

### Function Declaration
**C++ Only Interface Functions**
You can declare virtual C++ functions without the [[UE4 Macros|UFUNCTION specifier]]. These functions must be virtual so that you can override them in classes that implement your interface.
```
public:
virtual bool Pick();
```

You must then provide a default implementation in the interface's cpp.
```
bool IPickable::Pick()
{
    return false;
}
```

To implement the interface in an Actor class, you can create and implement an override specific to that class:
```
Pickup.h
public:
virtual bool Pick() override;

Pickup.cpp
bool Pickup::Pick()
{
    ...
    return false;
}
```

**Blueprint Callable Interface Functions**
To make a blueprint callable interface function, you must provide a [[UE4 Macros|UFUNCTION specifier]] with the **BlueprintCallable** specifier. You must also use either the BlueprintImplementableEvent or BlueprintNativeEvent specifiers and ==the function must not be virtual==.

- Functions using BlueprintCallable can be called in C++ or Blueprint using a reference to an object that implements the interface.
- If the function is void, the blueprint will consider it an event. To avoid this, you can make the function return a bool.

- Functions using BlueprintImplementableEvent can not be overridden in C++, but can be override in any Blueprint class that implements or inherits the interface.
```
public:
/**A version of Pick that can be implemented in Blueprint only. */
UFUNCTION(BlueprintCallable, BlueprintImplementableEvent, Category=Pick Interface)
bool Pick();
```
- Functions using BlueprintNativeEvent can be implemented in C++ by overriding a function with the same name, but with the suffix *_Implementation* added to the end. This specifier also allows implementations to be overridden in Blueprint.
```
public:
/**A version of Pick that can be implemented in Blueprint and C++. */
UFUNCTION(BlueprintCallable, BlueprintNativeEvent, Category=Pick Interface)
bool Pick();
bool Pick_Implementation();
```

### Execute a method from the interface
**C++ Only Interface Functions**
To execute a C++ Only method, just call the implemented method.

**BlueprintNativeEvent Interface Functions**
```
IPickable::Execute_Pick(instigatorActor, other params);
```

### Determining if a class implements an interface
Any of the following functions will check if a class implements an interface:
```
bool bIsImplemented = OriginalObject->GetClass()->ImplementsInterface(UPickable::StaticClass()); // bIsImplemented will be true if OriginalObject implements UPickable.

bIsImplemented = OriginalObject->Implements<UPickable>(); // bIsImplemented will be true if OriginalObject implements UPickable.

IPickable* ReactingObjectA = Cast<IPickable>(OriginalObject); // ReactingObject will be non-null if OriginalObject implements IPickable.
```

### Casting to other Unreal Types
UE4 casting system supports casting from one interface to another, or from an interface to an Unreal type.
```
// Casting an object to an interface
IPickable* MyInterface = Cast<IPickable>(OriginalObject); // ReactingObject will be non-null if the interface is implemented.

// Casting an interface to another interface
ISomeOtherInterface* DifferentInterface = Cast<ISomeOtherInterface>(MyInterface); // DifferentInterface will be non-null if MyInterface is non-null and also implements ISomeOtherInterface.

// Casting an interface to an object
AClass* Actor = Cast<AActor>(MyInterface); // Actor will be non-null if MyInterface is non-null and OriginalObject is an AClass or AClass-derived class.
```

### Implement interface via blueprint
To implement an interface via Blueprint, it must use the *Blueprintable* metadata specifier. Every interface function that the blueprint class wants to override must be either a *BlueprintNativeEvent* or a *BlueprintImplementableEvent*. Functions marked as *BlueprintCallable* will still be able to be called, but not overridden.

---
Planted: 2022-02-28
Last tended: 2022-02-28