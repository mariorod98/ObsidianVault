---
tags: state/seedling on/idleGames
---

# Idle Game - PVG
Las [[Idle Game Core Mechanics|mecánicas core]] de un Idle Game son:
- Un recurso que se recolecta mediante acciones del jugador y edificios.
- Este recurso se debe poder gastar en comprar edificios nuevos, subir de nivel edificios actuales y obtener mejoras para los edificios.
- Debe haber una mecánica de prestigio para resetear  el progreso a cambio de un bonus en la siguiente run.
- Pueden diseñarse diversas mecánicas para incrementar la interación durante el active time : popups que dan bonuses, habilidades con cooldown (pueden estar asociadas a edificios o no) que hacen que se generen más elementos o sea más rápido.

---
## Idle Cultist
- Recursos.
    - Víctimas. Las víctimas se obtienen a través de los adeptos. Los adeptos reclutan víctimas para ser sacrificadas.
    - Almas. Son la moneda del juego. Se obtienen sacrificando víctimas. Los sacrificios compran mejoras y edificios.
- Edificios.
    - Adeptos. Son los encargados de reclutar víctimas, cuanto mayor es su nivel, más rápido reclutan víctimas
    - Lugares de reclutamiento: Hideout, Library of dark arts, Necromancy classes... Aumentan el número de víctimas disponibles para ser abducidas.
    - Lugares de sacrificio: Pentagram, summoning ring, cursed church... están relacionados con las Almas.
- Gameloop de obtención de recursos:
    - Los lugares de reclutamiento atraen a víctimas.
    - Los adeptos abducen víctimas en los lugares de reclutamiento.
    - Las víctimas son sacrificadas en los lugares de sacrificio.
    - Esta cadena de montaje para obtener la moneda tiene tres cuellos de botella: el pool de víctimas inicial, la eficiencia de los adeptos y la eficiencia de los sacrificios. Est provoca que el jugador deba tomar decisiones estratégicas para identificar el cuello de botella actual y solventarlo.
- Mejoras:
    - Lugares de reclutamiento. Su eficiencia se mide por el número de víctimas que atraen por minuto.
        - Capacidad del lugar. Número de víctimas máximo.
        - Atracción del lugar. Número de víctimas atraidas cada minuto.
        - Genera un cuello de botella adicional entre ambas variables.
    - Adeptos. Su eficiencia se mide por el número de víctimas captadas por minuto.
        - Velocidad de captación.
        - Número de víctimas captadas en cada intento.
    - Lugares de sacrificio. Su eficiencia se mide por el número de Almas obtenidos por minuto.
        - Número de víctimas sacrificadas en cada sacrificio.
        - Velocidad de realización del sacrificio.
        - Almas obtenidas por víctima.
    - Mecánica de prestigio. Podría ser algo como irse a otra ciudad/país o ascender (as in cometer suicidio colectivo). Para resetear hay que entregar un número exorbitado de almas. Al resetear, se obtiene un modificador porcentual permanente sobre el valor base de todas las almas.
    - Otras mecánicas:
        - Alguna relacionada con la policía investigando el culto? Puede ser como un minijuego?
        - Popups que otorguen boosts temporales.
        - Misiones.
        - Añadir mecanicas de gestion


---
Planted: 2022-01-18
Last tended: 2022-01-18