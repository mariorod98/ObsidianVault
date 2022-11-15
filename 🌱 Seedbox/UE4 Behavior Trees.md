up:: [[⚙️Unreal Engine 4]]
tags:: #state/seedling #on/ue4/ai

# UE4 Behavior Trees

## What is a behavior tree?

## Behavior trees in UE4
A **UBehaviorTree** is an asset used to create artificial intelligence for non-player pawns. The behavior tree can be described as a set of rules and actions that will determine how a character behaves. 

Which rules are fired and which actions are performed is determined by a [[UE4 Blackboard]]. The **UBlackboard** contains all the info the tree needs to make a decision.

If a group of characters share the same behavior, they use the same Behavior Tree (not an instance of the tree for each character). Therefore, the Behavior Tree should not have variables that modify the path selected, as these will affect all the characters that share the same Behavior Tree.

To this end, Blackboards are used. A Blackboard is linked to a specific Pawn/Character and it stores all the variables related to that Pawn/Character that the Behavior Tree will use.

Behavior Trees are used by the [[AI Controller]] that possesses the Pawn/Character. This controller must have a **UBehaviorTreeComponent** that stores the BehaviorTree

## How to create a simple Behavior Tree
### Add the required modules
The first thing to do when using Behavior Trees is adding the correspondent modules to the ``Build.cs`` file:

```c#
PrivateDependencyModuleNames.AddRange(new string[] {
	"AIModule",
	"GameplayTasks"
});
```


## References
[Blackboard Documentation - Programming & Scripting / Blueprint - Unreal Engine Forums](https://forums.unrealengine.com/t/blackboard-documentation/1795)
---
Planted: 2022-09-27
Last tended: 2022-09-27