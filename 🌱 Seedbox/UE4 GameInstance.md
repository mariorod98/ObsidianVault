```cpp
UZeldaGameInstance* gm_instance = Cast<UZeldaGameInstance>(GetGameInstance());

gm_instance->acumulated_rupees_
```

```cpp
void AExamPlayerController::SetupInputComponent()  
{  
   Super::SetupInputComponent();  
  
   InputComponent->BindAction("DetectDoor", IE_Released, this, &AExamPlayerController::DetectDoor);  
   InputComponent->BindAxis("MoveVertical", this, &AExamPlayerController::MoveVertical);  
   InputComponent->BindAxis("MoveHorizontal", this, &AExamPlayerController::MoveHorizontal);  
}
```