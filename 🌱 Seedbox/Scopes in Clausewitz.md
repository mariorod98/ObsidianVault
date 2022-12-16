up:: [[⚔️ Cluasewitz Engine]]
tags:: #state/seedling #on/clausewitz 

# Scopes in Clausewitz
A scope is where exactly an [[Effects in Clausewitz|effect]] or [[Triggers in Clausewitz||trigger]] happens. Scopes are used to set the target of an effect or trigger. For example, the pops of a certain country or the building within a state. 

## Basic Scopes
- **ROOT**.
- **PREV**.
- **THIS**.
- **FROM**.

## Scope linking


## Scopes in different games
### Victoria 3
**State scope**
To scope to a [[States and State Regions in Victoria III|state]], use the letter *s*.

```
s:STATE_AMAZONAS = {
	add_homeland = brazilian
}
```

**Building scope**
The letter to scope a building is *b*. Although there is a building scope, in practice, game logic that involves buildings is done indirectly through the state scope. 
```
c:SIA = {
	any_scope_state = {
		state_region = s:STATE_NORTH_BORNEO
		any_scope_building = {
			is_building_type = building_sulfur_mine
			level >= 2
		}
	}
}
```


---
Planted: 2022-12-16
Last tended: 2022-12-16