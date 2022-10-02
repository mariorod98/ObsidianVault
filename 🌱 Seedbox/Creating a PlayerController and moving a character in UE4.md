up:: [[⚙️Unreal Engine 4]]
tags:: #state/seedling #on/ue4/tutorials

# Creating a PlayerController to move a character in UE4

## Defining the actions of the player
The [[Player Controller]] is used as an interface between the player's input and the character's actions. Therefore, the first thing to do is define the actions that the player will perform.

In this case, the player will be able to move in the vertical axis and perform a jump action. 

It is worth noting that the method `MoveHorizontal` accepts a float parameter while the method `Jump` does not. This is because the first method will be binded to an axis input, while the second will be binded to a button input. 

The axis input sends either 1.0 or -1.0 as the value, while the button input just calls the function whenever its pressed

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

The binding of the input and the actions is done in the overridden method `SetInputComponent`. 

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

---
Planted: 2022-09-26
Last tended: 2022-09-26