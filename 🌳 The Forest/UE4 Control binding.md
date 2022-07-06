up: [[⚙️Unreal Engine 4]]
tags: #state/bud #on/ue4

# UE4 Input binding
Input can be binded to the [[PlayerController]] or to a specific [[Actor]]. To be able to process input, the actor must have an active **UInputComponent**. Every [[Actor]] has an Input Component, but it is not initialized. However, the [[PlayerController]] has the component initialized.

In order for an actor to use the Input Controller, you must create the component using the method **CreateDefaultSubobject** in the constructor,

The binding is usually done in the BeginPlay of the actor. Before binding the input, you must enable it with the method **EnableInput**

## Types of mapping
- **ActionMapping**. Maps a discrete button or key press. The value is either Pressed (true) or Not Pressed (false).
- **AxisMapping**. Maps a keyboard, controller or mouse input to a continuous value (usually between -1 and 1, but these values can be modified).

## Input events
An *EInputEvent* is a define enum that determines the event from an input that will be bound to a specific method. The types of events supported are:
- **IE_Pressed**. When the input is pressed.
- **IE_Released**. When the input is released.
- **IE_Repeat**.  When the input is being pressed for several frames.
- **IE_DoubleClick**. When the input is double clicked (not very accurate).
- **IE_Axis**. When the input is an axis
- **IE_MAX**. ???
- 
## How to bind input
In order to bind input, you must first check that the Input Component has been created. Then, depending on the type of mapping (Action or Axis) you will use the methods **BindAction** and **BindAxis**. These bindings will be called in the **SetUpInputComponent** method (**SetupPlayerInputComponent** for actors).

==To bind a function to an input, the function must be UFUNCTION()==. The functions binded to an Action must be void and must not have parameters, while the functions binded to an Axis must also be void, but must have a float parameter, where the value of the axis will be stored.

When binding, you must provide the following information:
- The name of the input to bind,
- The type of event that will be bound (only for Actions).
- The instigator of the method.
- The method that will be called.
```cpp
// PlayerController example.

void AMyPC::SetupInputComponent() {
    Super::SetupInputComponent();

    InputComponent->BindAction("Jump", IE_Pressed, this, &AMyPC::Jump);
    InputComponent->BindAxis("MoveForward", this, &AMyPC::Move);
}


// Actor example.
void AMyActor::SetupPlayerInputComponent(class UInputComponent* PlayerInputComponent) {
    check(PlayerInputComponent)
    Super::SetupInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("Jump", IE_Pressed, this, &AMyActor::Jump);
    PlayerInputComponent->BindAxis("MoveForward", this, &AMyActor::Move);
}
```

## Order in which the input is consumed
When an input is received, the actors receive the input in an ordered manner. If the input is to be consumed (this means, only one actor will react to the input), then the first actor in the order will react to the input. ==Inputs are consumed by default==.

The order in which the input is received is the following:
1. The most recent actor to call the EnableInput method.
2. All the actors that belong to the corresponding PlayerController and have input enabled. The order is from newest actor to oldest.
3. The controller
4. The LevelScript.
5. The Pawn/Character possessed.

![[ue4_input_order.png]]

## Same input for multiple actors
When an actor receives an input, the default mode is to consume the input received, so it doesn't propagates to other actors. If you want to propagate a certain input, you can set the flag **bConsumeInput** to false when binding the input.
```cpp
InputComponent->BindAction("PressingA", IE_Released, this, &MyActorClass::AReleased).bConsumeInput = false;
```

---
Planted: 2022-05-09
Last tended: 2022-05-09