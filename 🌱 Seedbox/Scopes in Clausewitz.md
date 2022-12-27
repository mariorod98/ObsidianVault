up:: [[⚔️ Clausewitz Engine]]
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

**Culture scope**
[[Culture in Victoria III|Culture]] scope seems to work in a similar fashion to building scope, indirectly referenced. However, it has more use cases. To scope to a culture, use the letters *cu*.

```
state_region = {
	is_homeland = cu:greek
}
```

**Interest Group**
Scoping to an interest group is done using the letters *ig*.

```
ig:ig_landowners = {
	remove_ideology = ideology_paternalistic
	add_ideology = idology_republican_paternalistic
}
```

**Market Good scope**
Scoping to a market good is done using the letters *mg*.

```
mg:tools = {
	save_scope_as = cool_tools
}
```


## References
[Scopes - Victoria 3 Wiki](https://vic3.paradoxwikis.com/Scopes)

---
Planted: 2022-12-16
Last tended: 2022-12-16