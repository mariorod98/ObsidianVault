---
tags: state/seedling on/ue4
---

# UE4 Core Classes
There are four main class types that you derive from for the majority of gameplay classes. New classes that do not derivate from these core classes can be developed, but they will not participate in the features that are built into the engine.
## UObject
- UObject is the base building block of UE4. 
- Any class that inherits from UObject has a singleton UClass created for it that contains all of the metadata about the class instance.
- This class provides some of the most important base services in the engine:
    - Reflection of properties and methods.
    - Serialization of properties.
    - Garbage collection.
    - Finding UObjects by name,
    - Configurable values for properties.
    - Networking support for properties and methods.
- Classes that inherit directly from UObject start with a U.
## AActor
- An AActor is an object that is placed in the world (scene).
- It is either placed in a level in the editor or created at runtime via gameplay systems.
- AActor derives from UObject, so it inherits all its functionality. 
- AActors can be explicitly destroyed via code or via the garbage collector when the owning level is unloaded from memory.
- All AActors must have a root USceneComponent, which contains the translation, rotation and scale of the AActor.
- All classes that inherit directly from Actor start with an A.

## UActorComponent
- UActorComponents are responsible for the functionality that is shared across many types of AActors.
- They must be parented to an AActor. 
- Any UActorComponent attached to an Actor has a location, rotation and scaling relative to its parent.
- Some uses for UActorComponents include:
    - Visual meshes.
    - Particle effects.
    - Physics interactions.
    - Movement logic.
## UStruct
- A UStruct is a specialized version of a C++ struct and is used as a collection of related data.
- UStructs do not require extending any class. When declaring a C++ struct, just add the macro `USTRUCT()`.
- UStructs are not deleted by the garbage collector. If you create dynamic instances, you must manage their life cycle.
## UGameInstance
- This class is used to create singleton classes in UE4.

## USaveGame

## ALevelScriptActor

---
Planted: 2022-01-10
Last tended: 2022-03-21