up: [[⚙️Unreal Engine 4]]
tags: #state/bud #on/ue4

# UE4 Components
A Component is a special type of [[Object]] that [[Actors]] can attach to themselves as sub-objects. The base class for all components is `UActorComponent`. Everything the player sees or interacts with is the work of some type of component.

## Types of components
- **Actor Components** (class `UActorComponent`) do not have a transform. They are used for abstract behaviors that don't have physical representation. For example, movement, inventory management, etc.
- **Scene Components** (class `USceneComponent`, inherits from  `UActorComponent`) supports location-based behaviors that do not require geometric representation. For example, cameras, audio, physical forces, etc.
- **Primitive Components** (class `UPrimitiveComponent`, a child of `USceneComponent`) are Scene Components with geometric representation, either for rendering or collision purposes. For example, meshes, sprites, particle systems, etc.

## Examples
### Adding a Scene Component to a class
1. Add the component to the class declaration as a pointer. Do not forget to add the UPROPERTY.
```cpp
// ASpaceshipCharacter.h
class ASpaceshipCharacter {
	UPROPERTY(VisibleAnywhere, BlueprintReadWrite)
	class UWeaponComponent* weaponComp_;
}
```
2. Create the componennt in the class constructor and attach it to another component or set as root component.
```cpp
ASpaceshipCharacter::ASpaceshipCharacter()
{
	weaponComp_ 
}
```
---
Planted: 2022-01-16
Last tended: 2024-03-01
