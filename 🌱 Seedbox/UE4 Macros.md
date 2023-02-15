up: [[⚙️Unreal Engine 4]]
tags: #state/seedling #on/ue4

# UE4 Macros
- **UCLASS( )**: Used to tell Unreal to generate reflection data for a class. The class must derive from [[UE4 Core Classes#UObject|UObject]]. The UCLASS specifiers are:
    -  *Abstract*: Declares that the class is abstract, preventing the user from adding Actors of this class to Levels.
    - *Blueprintable*: This class can be extended by a Blueprint. The default is NotBlueprintable, unless inherited otherwise.
    - *BlueprintType*: Exposes this class as a type that can be used for variables in Blueprints.
- **USTRUCT( )**: Used to tell Unreal to generate reflection data for a [[UE4 Core Classes#UStruct|UStruct]].
- **GENERATED_BODY( )**: Replaced in UE4 with all the necessary boilerplate code that gest generated for the type.
- **UPROPERTY ()**: Enables a member variable of a UCLASS or a USTRUCT to be used as a [[UPROPERTY]]. The UPROPERTY specifiers are:
    - *BlueprintReadOnly*: this property can be read from a Blueprint, but not written to.
    - *BlueprintReadWrite*: This property can be read or written from a Blueprint.
    - *Category="TopCategory|SubCategory|..."*: Specifies the category of the property when displayed in Blueprint editing tools.
    - *EditAnywhere*: Indicates that this property can be edited by property windows, on archetypes and instances.
    - *EditDefaultsOnly*: Indicates that this property can be edited by property windows, but only on archetypes.
    - *EditInstanceOnly*: Indicates that this property can be edited by property windows, but only on instances, not on archetypes.
    - *BlueprintAssignable*.
    - *BlueprintAuthorityOnly*.
    - *Replicated*. Indicates that this property will be replicated to all the Clients.
- **UFUNCTION( )**: Enables a class method of a UCLASS or a USTRUCT to be used as a [[UFUNCTION]]. The UFUNCTION specifiers are:
    - *BlueprintCallable*: This function can be called from Blueprints.
- **UENUM( )**: Used to tell Unreal to generate reflection data for an enum.
---
Planted: 2022-02-07
Last tended: 2022-02-07