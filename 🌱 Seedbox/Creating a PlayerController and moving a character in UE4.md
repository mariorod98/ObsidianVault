up:: [[⚙️Unreal Engine 4]]
tags:: #state/seedling

# Creating a PlayerController to move a character in UE4

## Defining the actions of the player
The [[Player Controller]] is used as an interface between the player's input and the character's actions. Therefore, the first thing to do is define the actions that the player will perform.

In this case, the player will be able to move in two axis: vertical and horizontal.

```c++
class AMyPlayerController : public APlayerController
{
	GENERATED_BODY()

public:
	UFUNCTION()
	void MoveVertical(float direction);
	
	UFUNCTION()
	void MoveHorizontal(float direction);
}
```

**It is crucial that the functions are declared as [[UFUNCTION]], because it will be later binded to the ImputComponent.**

## Binding the actions to the input


---
Planted: 2022-09-26
Last tended: 2022-09-26