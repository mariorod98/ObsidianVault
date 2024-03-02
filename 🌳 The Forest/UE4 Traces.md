up: [[⚙️Unreal Engine 4]]
tags: #state/bud #on/ue4

# UE4 Traces
Traces are a method of getting collision feedback on a specific area. They are defined by a starting point, an ending point and an area that traverses both points.

In order to get collision information, traces use the physics and collision system of UE4. Therefore, only the objects that are correctly configured will be detected by the trace. In other words, they must have either Query or Collisions enabled.

## Types of traces
**Traces by type of detection.**
Traces use the physics system. In order to create a trace, you must define the category you want to trace against. There are three categories:
- **ByChannel** uses the [[CollisionChannel]] specified.
- **ByObjectType** Uses a specific [[collision ObjectType]].
- **ByProfile** uses a specific [[Profile]].

**Traces by complexity.**
When tracing, you can choose to return:
- **Test**. If the traces has collided with an object or not. Doesn't return hit information. It is the cheapest.
- **Single**. Returns the hit result of the first element detected by the trace.
- **Multi**. Returns the hit result of all the elements detected by the trace

==When using Multi Trace by channel, the trace will return all Overlaps up to and including the first Block==.

**Traces by shape.**
The base trace is a *Line Trace*, but this might not be enough in some instances. For example, when creating a vision cone for an enemy. In this instance, you can use a *shape trace*. There are three shape traces: *Sphere Trace*, *Capsule Trace* and *Box Trace*.

## Trace Params
When calling a trace, you can specify a set of parameters by creating a *FCollisionQueryParams* structure and passing it to the function. Some of the most importants params are:
- *bTraceComplex*. Wether we should tace against complex collisions.
- *MobilityType*. Filters the query by mobility type (static vs stationary/movable).
- *bReturnPhysicalMaterial*. Whether we want to include the physical material in the hit results.
- *AddIgnoredActor\<s\>()*. Add an actor for this trace to ignore.

## Hit Results
The *FHitResult* is the structure that stores all the information about a collision. Some of its most important attributes and methods are:
- *bBlockingHit*. Indicates if this hit was a result of blocking collision.
- *BoneName*. The name of the bone hit (for skeletal meshes).
- *Component*. The [[PrimitiveComponent]] hit by the trace.
- *Distance*. The distance from TraceStart to the Location in world space.
- *ImpactNormal* or *Normal*. Normal of the hit in world space.
- *ImpactPoint*. Location in world space of the actual contact of the trace shape with the impacted object.
- *Location*. The location in world space where the moving shape would end up agains the impacted object.
- *PhysMaterial*. PhysicalMaterial that was hit.
- *TraceEnd*. End location of the trace.
- *TraceStart*. Start location of the trace.
- *GetActor()*. Returns the actor that owns the component that was hit.
- *GetComponent()*. Returns the component that was hit.

## Calling a trace
First we need to create the FCollisionQueryParams and the FHitResult structures.
```cpp
FCollisionQueryParams TraceParams(FName(TEXT("CheckSlopes")), false);
TraceParams.bReturnPhysicalMaterial = false;
TraceParams.bTraceComplex = false;
TraceParams.AddIgnoredActor(GetOwner());

FHitResult HitResult;
```

Depending on the type of trace that we want to use, we will call a specific function. All the traces functions belong to the UWorld class, to access them you must use *GetWorld()*. Moreover, all traces return a bool determining if there was a hit or not.
```cpp
if(GetWorld()->LineTraceSingleByChannel(HitResult, StartTrace, EndTrace, ECC_WorldStatic, TraceParams)) {
    // ...
}
```

## Types of traces
```cpp
// Returns the hit with the first element collided
GetWorld()->LineTraceSingleByChannel(HitResult, StartTrace, EndTrace, TraceChannel, TraceParams);

// Returns the hit of all the elements collided
GetWorld()->LineTraceMultiByChannel(OutHits, StartTrace, EndTrace, TraceChannel, TraceParams, ResponseParams);

// Sweeps a shape and returns if a hit is found
GetWorld()->SweepTestByChannel(Start, End, Rotation, TraceChannel, CollisionShape, QueryParams);

// Sweeps a shape and returns all the overlaps until the first blocking hit (included). After the first hit, no test will be done
GetWorld()->SweepMultiByProfile(OutHits, Start, End, Rotation, ProfileName, CollisionShape, QueryParams);

// Test the collision of a shape and returns if any blocking or overlappin shape is found
GetWorld()->OverlapAnyTestByChannel(Position, Rotation, TraceChannel, CollisionShape, QueryParams, ResponseParams);

// Test the collision of a shape and determine the set of components that it overlaps
GetWorld()->OverlapMultiByProfile(OutOverlaps, Position, Rotation, ProfileName, CollisionShape, QueryParams);

// Sweep the geometry of the supplied component and determine the set of components that it hits
GetWorld()->ComponentSweepMulti(OutHits, PrimComp, Start, End, rotation, QueryParams);

// Test the collision of the supplied component using a specific channel and determine the set of components that it overlaps
GetWorld()->ComponentOverlapMultiByChannel(OutOverlaps, PrimComp, Position, Rotation, TraceChannel, QueryParams, ObjectQueryParams);
```

## Examples
### Calling a trace by channel using a collision shape
```cpp
// BombDrop.cpp

void ABombDrop::Explode()
{
	// Initialize all the call's params
	FCollisionShape sphere = FCollisionShape::MakeSphere(explosion_radius_);
	TArray<FOverlapResult> overlap_results;
	FCollisionQueryParams params;
	params.TraceTag = TEXT("explosion_trace");
	
	// Call the trace
	GetWorld()->OverlapMultiByChannel(overlap_results, GetActorLocation(), FQuat::Identity, ECC_GameTraceChannel2, sphere, params);

	// Iterate through the results
	for(int i = 0; i < overlap_results.Num(); ++i)
	{
		AEnemy* enemy = Cast<AEnemy>(overlap_results[i].GetActor());
		if(enemy != nullptr)
		{
			GLog->Log(enemy->GetName());
			FVector direction = enemy->GetActorLocation() - GetActorLocation();
			direction.Normalize();
			enemy->Hit(damage_, direction);
		}
	}
	Destroy();
}
```


---
Planted: 2022-04-19
Last tended: 2022-09-04