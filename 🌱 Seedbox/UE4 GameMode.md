up::
tags:: #state/seedling #on/ue4


# UE4 GameMode
- Define las reglas del juego.
- No permanece entre escenas
- Puede hacerse un override por nivel

# UE4 GameInstance
- Singleton. No se destruye entre escenas
- Gestiona carga de niveles

# UE4 Player controller
- Maneja la camara
- Contiene un HUD
- 

UCustomGameInstance* GI = Cast<UCustomGameInstance>(UGameplayStatics::GetGameInstance(GetWorld()));

---
Planted: 2022-02-14
Last tended: 2022-02-14