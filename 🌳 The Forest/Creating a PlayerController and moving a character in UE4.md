up:: [[⚙️Unreal Engine 4]]
tags:: #state/bud #on/ue4/tutorials

# Creating a PlayerController to move a character in UE4

## Defining the actions of the player
The [[PlayerController]] is used as an interface between the player's input and the character's actions. Therefore, the first thing to do is define the actions that the player will perform.

In this case, the player will be able to move in the vertical axis and perform a jump action. 

It is worth noting that the method `MoveHorizontal` accepts a float parameter while the method `Jump` does not. This is because the first method will be binded to an axis input, while the second will be binded to a button input. 

```c++
// MyPlayerController.h
class AMyPlayerController : public APlayerController
{
	GENERATED_BODY()

public:
	UFUNCTION()
	void MoveHorizontal(float direction);

	UFUNCTION()
	void Jump()
}
```

**It is crucial that the functions are declared as [[UFUNCTION]], because they will be later binded to the ImputComponent.**

## Binding the actions to the input

The binding of the input and the actions is done in the overridden method `SetInputComponent`. Depending on the type of input (axis or action) the binding may change:

```c++
BindAction(
	FName - name of the action, 
	EInputEvent - type of event, 
	UserClass* - object that will execute the method,
	FMethodPtr -  pointer to the method
);

BindAxis(
	FName - name of the axis, 
	UserClass* - object that will execute the method,
	FMethodPtr -  pointer to the method
);
```

The types of events that the input acepts are:
- IE_Pressed
- IE_Released
- IE_Repeat
- IE_DoubleClick
- IE_Axis

```c++
// MyPlayerController.h

class AMyPlayerController : public APlayerController {
	...
	void SetInputComponent() override;
	...
}

// MyPlayerController.cpp

void AMyPlayerController::SetupInputComponent() {
	Super::SetupInputComponent();
	InputComponent->BindAction("Jump", IE_Pressed, this, &AMyPlayerController::Jump);
	InputComponent->BindAxis("MoveHorizontal", this, &AMyPlayerController::MoveHorizontal);
}

```

## Implementing the APlayerController methods
In this simple example, the PlayerController methods are wrapper methods to call those of the Character. It is important to remember that, **before calling the character methods, we must first cast the pawn to the character and check if the casting is correct**.

```c++
// MyPlayerController.cpp

void AMyPlayerController::Jump() {
	APlayerCharacter* player = Cast<APlayerCharacter>(GetPawn());
	if(player)
		player->Jump();
}

void AMyPlayerController::MoveRight(float Value) {
	APlayerCharacter* player = Cast<APlayerCharacter>(GetPawn());
	if(player)
		player->MoveRight(Value);
}
```

## Implementing the methods in APlayerCharacter
The last step is to implement the methods that are called from the PlayerController (unless we called methods already implemented in the engine).

```c++
// PlayerCharacter.h
class APlayerCharacter : public ACharacter {
	...
	void Jump() override;
	void MoveHorizontal(float direction);
	...
}

// PlayerCharacter.cpp
void APlayerCharacter::Jump() {
	if (can_jump_) {
		is_jumping_ = true;
		ACharacter::Jump();
	}
}

void APlayerCharacter::MoveRight(float Value) {
	// add movement in that direction
	AddMovementInput(FVector(0.f, -1.f, 0.f), Value);
}
```

---
Planted: 2022-09-26
Last tended: 2022-10-02