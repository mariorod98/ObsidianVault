---
tags: state/seedling
---

# UE4 Optimization tips
- The ```Tick``` function is very costly and it must be avoided at all cost. If an actor doesn't use the ```Tick``` function, there is an option in its details called ```Start with Tick Enabled``` that can be unchecked to omit the call to ```Tick```.
- Blueprints code is very inefficient. Nevertheless, it can be used to modify component variables.
---
Planted: 2022-01-17
Last tended: 2022-01-17