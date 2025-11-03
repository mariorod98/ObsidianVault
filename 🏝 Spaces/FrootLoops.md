# Concept
**Arrange boxes of froot loops as fast as possible.** 

- Each box has a countdown to fill the box. 
- If you do not finish it, you lose. 
- Each box goes faster than the previous OR it has more loops
- You get a high score depending on the number of loops arranged.

## DAY 1

Core loop:
1. Box content drops to the table
2. Arrange box content by taking each individual loop to its colour bowl as fast as possible
3. If table is cleaned in time, restart countdown
4. If not, lose


**TASKS**
Gameplay
- DONE Actions: pick loop, move loop, drop loop.
- DONE Spawning of loops.
- DONE Despawning of loops when moved to the correct bowl.

Game manager that tracks
- DONE Countdown and fail state
- DONE Handle score, wrongly inserted loops remove score!!
- DONE When table is clean, put next box

Base UI
- DONE Current score
- DONE number of loops left
- DONE time left
- DONE number of boxes emptied

Art
- DONE bowls of different colors
-DONE  froot loops 3d models or 2d images (3d would be funnier tho)


## DAY 2
To make the gameplay more interesting, there should be some kind of power ups that help you and a way to unlock them. 

I have two variants in mind:
- Similar to vampire survivor, each box you clean you get to choose between three different power ups
- Similar to match-3 games, when you perform some action ingame, it has a powerful effect

Power ups:
- Magnet that attracts all loops of the same 

**TASKS**
DESIGN
- Define power ups and drawbacks


GAMEPLAY
- DONE Fix drag and drop feeling
- DONE Add respawn trigger under the table
- DONE Add increase difficulty each round
- DONE Track total loops consumed 
UI
- Menu to pick power up
- DONE Start menu
- DONE End menu
- DONE Add icons to hud

OTHERS
- Add background



## DAY 3
Make the drag and drop mechanic feel good. Add juice, polish and fix bugs.

**TASKS**
- MAYBE obligar a aumentar color cada x rondas

-cuando entran cuenco, que no se puedan volver a coger
- si loop incorrecto entra en cuenco, respawn
- cuando loop entra en cuenco, se almacena el score que se ha dado, si sale, se elimina ese score

- que los loops no sumen puntos mientras esten cogidos
- delay entre terminar ronda y mostrar opciones
- cambiar masa de los loops o gravedad

- make far away loops get attracted to center of hand
- make loops disappear one by one
- Que el countdown tarde un par de segundos en empezar
- add multiplier to hud

Gameplay
- Make loops wrongly put in a bowl disappear?
- Implement the powerups
	- DONE Increment pick radius
	- Increment magnetic bowl attraction
	- DONE Increase time
	- DONE Increase score bonus for putting loops of same color
	- DONE Increase score bonus the first 5 seconds
	- increase bowl sizes
	- Make scoring give you extra time

- Implement the drawbacks
	- DONE Increment loop count
	- DONE Increment loop bounciness
	- DONE Add color
	- DONE Increment loop size variation
	- Add chance of a loop to explode

- Make brief tutorial

- Make loops in incorrect bowl disappear?
- Make loops in incorrect bowl get ejected?
- Increase bowl trigger upwards  
- Store highscore

- Reduce music
- Restart score

Sound
- pick and drop frootloop
- New box drops frootlops
- Box completed
- Frootloot correctly assembled
- music
- more sound effects (each loop color a different note or different but similar sound)

Others
- Add more juice: particles/effects