---
tags: state/seedling on/ue4/interface
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
class ATrap : public AActor, public IReactToTriggerInterface
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
virtual bool ReactToTrigger();
```

You can then provide a default implementation in the interface's cpp.
```
bool IReactToTriggerInterface::ReactToTrigger()
{
    return false;
}
```

To implement the interface in an Actor class, you can create and implement an override specific to that class:
```
ATrap.h
public:
virtual bool ReactToTrigger() override;

ATrap.cpp
bool ATrap::ReactToTrigger()
{
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
/**A version of React To Trigger that can be implemented in Blueprint only. */
UFUNCTION(BlueprintCallable, BlueprintImplementableEvent, Category=Trigger Reaction)
bool ReactToTrigger();
```
- Functions using BlueprintNativeEvent can be implemented in C++ by overriding a function with the same name, but with the suffix *_Implementation* added to the end. This specifier also allows implementations to be overridden in Blueprint.
```
public:
/**A version of React To Trigger that can be implemented in Blueprint only. */
UFUNCTION(BlueprintCallable, BlueprintNativeEvent, Category=Trigger Reaction)
bool ReactToTrigger();
bool ReactToTrigger_Implementation();
```

### Execute a method from the interface
**C++ Only Interface Functions**
```

```
**BlueprintNativeEvent Interface Functions**

### Determining if a class implements an interface
Any of the following functions will check if a class implements an interface:
```
bool bIsImplemented = OriginalObject->GetClass()->ImplementsInterface(UReactToTriggerInterface::StaticClass()); // bIsImplemented will be true if OriginalObject implements UReactToTriggerInterface.

bIsImplemented = OriginalObject->Implements<UReactToTriggerInterface>(); // bIsImplemented will be true if OriginalObject implements UReactToTriggerInterfacce.

IReactToTriggerInterface* ReactingObjectA = Cast<IReactToTriggerInterface>(OriginalObject); // ReactingObject will be non-null if OriginalObject implements UReactToTriggerInterface.
```

### Casting to other Unreal Types
UE4 casting system supports casting from one interface to another, or from an interface to an Unreal type.
```
IReactToTriggerInterface* ReactingObject = Cast<IReactToTriggerInterface>(OriginalObject); // ReactingObject will be non-null if the interface is implemented.

ISomeOtherInterface* DifferentInterface = Cast<ISomeOtherInterface>(ReactingObject); // DifferentInterface will be non-null if ReactingObject is non-null and also implements ISomeOtherInterface.

AActor* Actor = Cast<AActor>(ReactingObject); // Actor will be non-null if ReactingObject is non-null and OriginalObject is an AActor or AActor-derived class.
```

### Implement interface via blueprint
To implement an interface via Blueprint, it must use the *Blueprintable* metadata specifier. Every interface function that the blueprint class wants to override must be either a *BlueprintNativeEvent* or a *BlueprintImplementableEvent*. Functions marked as *BlueprintCallable* will still be able to be called, but not overridden.

---
Planted: 2022-02-28
Last tended: 2022-02-28