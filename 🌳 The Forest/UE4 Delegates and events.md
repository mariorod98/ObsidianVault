up: [[⚙️Unreal Engine 4]]
tags: #state/bud #on/ue4/events

# UE4 Delegates and events

## Delegates
**Delegates are a generic and safe way to call member functions on C++ objects.** 

### Types of delegates
- **Single delegates** can only bind one function. They act as a function pointer.
- **Multicast delegates** can bind to several functions. When executed, they will call all the functions bound. ==They cannot use return values==. Multicast delegates acts as an array of delegates, so it uses array-like semantics in its methods (Add instead of Bind, Remove instead of Unbind...).
- **Dynamic delegates** can be serialized and their functions can be found by name. ==They are slower than regular delegates.== They can be single and multicast.

### Declaring delegates
To create a delegate, you must use one of the MACROS that UE4 defines to create the signature. The macro will depend on the type of delegate, the number of parameters and whether it returns a value or not. ==Delegates are declared in the broadcaster class==
```cpp
// Single delegate
DECLARE_DELEGATE...
// Multicast delegate
DECLARE_MULTICAST_DELEGATE...
// Dynamic single delegate
DECLARE_DYNAMIC_DELEGATE...
// Dynamic multicast delegate
DECLARE_DYNAMIC_MULTICAST_DELEGATE...

DECLARE_..._DELEGATE(Name)
DECLARE_..._DELEGATE_OneParam(DelegateName, ParamType, ParamName)
DECLARE_..._DELEGATE_<Num>Params(DelegateName, ParamType1, ParamName1, ...)

DECLARE_..._DELEGATE_RetVal(RetValType, DelegateName)
DECLARE_..._DELEGATE_RetVal_OneParam(RetValType, DelegateName, ParamType, ParamName)
DECLARE_..._DELEGATE_RetVal_<Num>Params(RetVal Type, DelegateName, ParamType1, ParamName1, ...)
```

UDelegates support the same specifiers as UFunctions, but you must use UDELEGATE() instead of UFUNCTION. Usually, the delegate name starts with the letter F.
```cpp
UDELEGATE(BlueprintAuthorityOnly)
DECLARE_DYNAMIC_DELEGATE(FMyDelegate)
```

After defining the signature, you can create the delegate as an attribute of the class, with the same return value and parameters specified in the macro. The attribute must have the UPROPERTY specifier.
```cpp
DELCARE_DELEGATE_OneParam(FOnHit, AActor*, actor)
...
UPROPERTY(BlueprintAssignable, Category="Delegates")
FOnHit OnPlayerHit;
```

### Binding delegates
Once you have created a delegate, you must bind the functions you want the call once the delegate is executed. The binding function depends on the type of delegate created.

**Single delegates**
```cpp
DelegateName.Bind(Instigator, Function);
OnPlayerHit.Bind(this, Player::OnHit);
```

**Multicast delegates**
```cpp
DelegateName.Add(Instigator, Function);
OnPlayerHit.Add(this, Player::OnHit);
```

**Single dynamic delegates**
```cpp
DelegateName.BindDynamic(Instigator, Function);
OnPlayerHit.BindDynamic(this, Player::OnHit);
```

**Multicast dynamic delegates**
```cpp
DelegateName.AddDynamic(Instigator, Function);
OnPlayerHit.AddDynamic(this, Player::OnHit);
```

To check if a delegate has bound objects, you can use the following methods:
```cpp
OnPlayerHit.IsBound(); // returns true if ANY object is bound
OnPlayerHit.Contains(this, "methodName") // only for multicast events
```


### Executing delegates
When executing a delegate, all the functions bound to it will be called.  There is no difference between dynamic and non-dynamic delegates.

**Single delegates**
==It is crucial to check if the single delegate is bound before executing it.== Otherwise, if a single delegate has no bindings and is called, an assertion will be triggered.
```cpp
if(OnPlayerHit.IsBound()) {
    OnPlayerHit.Execute(param1, param2,...);
}

// Alternatively, the method ExecuteIfBind does the check inside
OnPlayerHit.ExecuteIfBound(param1, param2,...);
```

**Multicast delegates**
Multicast delegates are safe to execute, even if nothing is bound. The execution order of the bound functions is not defined. It may not be in the order the functions were added.
```cpp
OnPlayerHit.Broadcast(param1, param2,...);
```

### Unbinding delegates
It is important to unbind a function from a delegate when the object that contains the function is going to be destroyed. 

**Single delegates**
```cpp
OnPlayerHit.Unbind();
```
**Multicast delegates**
```cpp
OnPlayerHit.Remove(instigator, "FunctionName");
OnPlayerHit.RemoveAll();
```
**Single and multicast dynamic delegates**
```cpp
OnPlayerHit.RemoveDynamic(instigator, "FunctionName");
```

## Events
Events are a type of multicast delegate. The main difference between delegates and events is that the methods ``Broadcast``, ``IsBound`` and ``Clear`` are public in the first one, while they are private in the latter. This means that, when creating an event, only the class that stores that event can trigger it. With delegates, any other class can call the delegate, as it is public.

Events share the same methods as multicast delegates, so all the steps to create, bind, execute and unbind an event are performed in the same manner as with multicast delegates. The only significant difference is the macro used when declaring the event.

### Declaring events
Events are declared using almost the same syntax as multicast delegates, but with a different MACRO name. The first parameter of the macro is the class which will own the event, and thus the only class that will be able to call  ``Broadcast``.

```cpp
DECLARE_EVENT(OwningType, EventName)
DECLARE_EVENET_OneParam(OwningType, EventName, Param1Type, Param1Name)
DECLARE_EVENT_<Num>Params(OwningType, EventName, Param1Type, Param1Name,...)
```


---
Planted: 2022-04-18
Last tended: 2022-04-18