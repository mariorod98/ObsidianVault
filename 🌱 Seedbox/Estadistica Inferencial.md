---
created: 2026-04-05
last updated: 2026-04-05
---

up::
tags:: #state/seedling

# Estadistica Inferencial
Rama de al estadística que estudia las características de una población a partir de una muestra finita de datos de la población. 

## Contraste de hipótesis
El contraste de hipótesis parte de una pregunta de investigación y sigue con un conjunto de pasos muy definidos.

Ejemplos de preguntas:
1. ¿El peso al nacer de hijos de mujeres de nacionalidad española es diferente de 3110 gramos?

Ante cualquier pregunta de investigación, hay dos hipótesis:
- $H_0$, La hipótesis nula: el valor medio de peso al nacer de los niños de mujeres
españolas en 2020 es igual a 3110 gramos.
- $H_1$, la hipótesis alternativa: el valor medio de peso al nacer de los niños de
mujeres españolas en 2020 es diferente de 3110 gramos.

El desarrollo del test de hipótesis se realiza por refutación. Consiste en buscar si hay evidencia suficiente ([[nivel de confianza]]) para rechazar la hipótesis nula.

### Hipótesis nula e hipótesis alternativa
A partir de la pregunta de investigación, debemos definir dos hipótesis. Nuestro test estadístico nos informará sobre qué hipótesis escogeremos para responder a la pregunta.

La **hipótesis nula**, $H_0$, es la hipótesis de partida. Debe recoger el hecho que queramos someter a prueba.

La **hipótesis alternativa**, $H_1$, es la que se ofrece como alternativa a la nula. Representa que se ha producido un cambio con respecto a la situación descrita en la hipótesis nula.

La hipótesis alternativa puede ser de dos tipos:
- **Hipótesis bilateral**. Si el parámetro es diferente de la hipótesis nula. 
- **Hipótesis unilateral**. Si solo se compara una dirección.

> [!Ejemplo]
> **Pregunta de investigación:**  ¿La media de edad de las personas que sobrevivieron en el Titanic es igual que la media de edad de las personas que no sobrevivieron?
> 
> **Hipótesis nula:** La media de las personas que sobrevivieron en el Titanic es igual que la media de las que no sobrevivieron. $H_0: \mu_{survived} = \mu_{not\_survived}$
> 
> **Hipótesis alternativa bilateral:** La media de las personas que sobrevivieron en el Titanic es distinta de las que no sobrevivieron. $H_1: \mu_{survived} \ne \mu_{not\_survived}$
> 
> **Hipótesis unilateral** La media de las personas que sobrevivieron en el Titanic es mayor que la media de las que no sobrevivieron.  $H_1: \mu_{survived} > \mu_{not\_survived}$

## Tipos de test
- **Paramétricos**
- **No paramétricos**

## Tipos de preguntas
**Contraste de hipótesis de una muestra**.  
*¿El peso al nacer de hijos de mujeres de nacionalidad española es diferente a 3110 gramos?*

Una única muestra de la que se quiere saber si un atributo tiene un valor específico. 

**Contraste de hipótesis de dos muestras independientes**. 
*¿El peso al nacer de los niños es significativamente diferente al peso de las niñas?* 

Tenemos la muestra niños y la muestra niñas. Son independientes porque se es niño o niña. Se compara el mismo atributo de ambos. En este caso, es un contraste bilateral.

**Contraste de hipótesis de dos muestras independientes sobre la varianza**. 
*¿El peso al nacer de los niños varía igual que el peso de las niñas?*

Aquí, se pregunta por la variabilidad del atributo en dos muestras independientes.

**Test sobre la proporción**
*¿La proporción de niños es igual a la proporción de niñas?*

**Test sobre la proporción de dos muestras independientes**
*La proporción de niñas nacidos en la población, ¿Es la misma en España que en Francia?*

## Condiciones de la estadística diferencial
1. Una muestra representativa del conjunto global.
2. Un [[nivel de confianza]] a partir del que podemos afirmar que la hipótesis NO es falsa.

## Pasos para realizar un test estadístico
1. Formular la pregunta de investigación.
2. Recoger una muestra representativa de nacimientos.
3. Formular la hipótesis nula y alternativa.
4. Identificar los tests estadísticos disponibles y sus condiciones de aplicación (como por ejemplo la distribución de los datos).
5. Aplicar el test estadístico que permitirá realizar la inferencia. Si se cumplen las condiciones sobre la distribución de los datos, se puede aplicar un test paramétrico. De lo contrario, hay que elegir test no paramétricos.
6. Una vez aplicado el test, se concluye sobre el rechazo o no de la hipótesis nula.
7. Se da respuesta a la pregunta de investigación formulada.

## References

## Related notes