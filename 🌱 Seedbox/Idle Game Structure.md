Class GameManager
- unsigned int souls : current number of souls
- array bool active_buildings 
- array Building buildings

Class Building
- int base_cost: base cost of the building in souls
- float base_sacrifice_cooldown: base cooldown between sacrifices
- int base_victim_value: base value of the victims in souls
- int sacrifice_level: level of the sacrificial chamber
- int cooldown_level: level of cooldown reduction
- canBeUpgraded();
- upgrade()
- calculateCost()
- calculateVictimValue()
