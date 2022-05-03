---
tags: state/bud
---

# UE4 Timer
Timers are a useful tool to perform an action once (or repeatedly) at specified intervals. They can be used to set actions to happen on a delay or over a period of time. Timers can also be used to remove some burden from the Ticks.

**Timers are not thread safe at the moment, and will cause an assert if accessed outside of the game thread.**

## FTimerManager
Timers are managed by the class *FTimerManager*. This class exists on the Game Instance Object and on each World Object.  The first will manage global timers, while the latter will manage timers related to that world In order to access it, you can use the following methods:
```
// For world timers
GetWorld()->GetTimerManager()
// or
GetWorldTimerManager()

// For global timers
UGameplayStatics::GetGameInstance()->GetTimerManager()
```
## FTimeHandle
*FTimeHandle* is an object whose function is handling a specific timer. They act as a reference to the timer.

## Create a timer
To create a timer, you must call the TimerManger method **SetTimer**. This methods admits the following params:
- **FTimerHandle**: handle that will reference to the created timer.
- **InObject**: object to call the timer function on.
- **InMethod**: method to call when timer fires. ==This method must have the macro UFUNCTION().==
- **Rate**: amount of time in seconds between timer set and firing.
- **bLoop** (optional): true to loop the timer, false to fire only once. Default is true.
- **firstDelay** (optional): time in seconds for the first delay in a looping timer, if <0, **Rate** will be used. Default is **Rate**.

```
FTimerHandle TimerHandle;
GetWorld()->GetTimerManager().SetTimer(TimerHandle, this, &AMyActor::CallMePlease, 10.0f, false)
```

To create a timer with parameters, you must use a *FTimerDelegate*, a child class of *TBaseDelegate*. This delegate is used as an interface between the timer and the method. To bind the method to the delegate, you must use **BindUFunction**. This methods accepts as params:
- **InObject**: the object to call the timer function on.
- **InMethod**: the method to call when timer fires.
- Ordered list of the values the params of **InMethod** will take.

```
FTimerDelegate myTimerDelegate;
FTimerHandle myTimerHandle;

myTimerDelegate.BindUFunction(this, Fname("CallMePlease"), 10.0f, 3);
GetWorldTimerManager().SetTimer(myTimerHandle, myTimerDelegate, 8.0f, true);
```

You can also use **SetTimerForNextTick** which will fire the given function in the next tick. Its only parameters are the **InObject** and **InMethod**.

## Clearing a timer
To clear a timer, you must call the method **ClearTimer** from *FTimerManager*, using the handle of the timer to be cleared. You can also use the method **ClearAllTimersForObject** to clear all the timers related to a specific object. ==It is important to clear timers related to objects that are being destroyed.==
```
GetWorldTimerManager().ClearTimer(TimerHandle);
GetWorldTimerManager().ClearAllTimersForObject(myObject);
```

##  Pausing and resuming a timer
Using the *FTimerManager* method **PauseTimer**  you can pause the given timer. This will prevent the timer from incrementing its counter and, while the elapsed and remaining times stay the same.

To resume the timer, you can use the method **UnpauseTimer**.

```
GetWorldTimerManager.PauseTimer(TimerHandle);
GetWorldTimerManager.UnpauseTimer(TimerHandle);
```

## Accesing timer information
In addition to managing timers, timer managers also provide functions for obtaining information for a specific timer.
- **IsTimerActive** is used to determine if the specified timer is currently active and not paused.
- **GetTimerRate** returns the current rate of a timer. It will return -1 if the timer handle is not valid.
-**GetTimerElapsed** returns the elapsed time for the associated timer. It will return -1 if the timer handle is not valid.
**GetTimerRemaining** returns the remaining time for the associated timer. It will return -1 if the timer handle is not valid.

---
Planted: 2022-05-03
Last tended: 2022-05-03