---
created: 2026-04-05
last updated: 2026-04-11
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

## The process of null hypothesis testing
- Step 1. Formulate a hypothesis of interest
- Step 2. Specify the [[null and alternative hypotheses]].
- Step 3. Collect some data.
- Step 4. Fit a model to the data and compute a test statistic.

## Caso de uso: Contraste de una muestra.
### 1. Formular pregunta de investigación
**Pregunta de investigación:** ¿Duermen los adolescentes más de 7 horas diarias en promedio?


### 2. Definir hipótesis nula y alternativa
**Hipótesis nula:** $H_0:\mu=7$
**Hipótesis alternativa:** $H_1:\mu>7$

### 3. Recoger mediciones de la muestra
Cálculo de la media, tamaño muestra y desviación típica.
$\overline{x}=7.37$
$s=0.82$
$n=35$

### 4. Hacer estadístico de contraste
Para este caso en particular, se aplica el test de una muestra sobre la media **asumiendo que la población sigue una distribución normal**, con varianza desconocida.

- El test es unilateral por la derecha, ya que la hipótesis alternativa es *mayor que*.
- Varianza desconocida porque no sabemos la varianza de la población.
- Asumimos que la población sigue una distribución normal debido al **teorema del límite central**. Al tomar muestras aleatorias de tamaño suficientemente grande ($n>30$), la distribución de las medias *muestrales* tiende a seguir una distribución normal cuya media es la media *poblacional* $\mu$ y desviación estándar $\dfrac{\sigma}{\sqrt{n}}$. Esto permite aplicar métodos estadísticos basados en la normalidad incluso cuando la población original no es normal.

Puesto que no conocemos la varianza, la debemos estimar a partir de la desviación típica. Por ello, bajo la hipótesis nula $H_0:\mu=7$,  el estadístico de contraste $t_{obs}$ que sigue una distribución t de Student con n-1 grados de libertad:

$t_{ obs}=\dfrac{\overline{x}-\mu_{0}}{\frac{s}{\sqrt{n}}}\sim t_{n-1}$

Trabajaremos con un nivel de confianza del 95% ($\alpha=0.05$)

Hay dos formas de calcular el rechazo de la hipótesis nula: 
- $t_{obs}>t_{1-\alpha}$, es decir, si el valor observado está en la región del 5% mayor que el umbral.
- $p<\alpha$, es decir, la probabilidad es menor que el nivel de significancia

### 5.1. Calcular el estadístico de contraste y el valor crítico

$t_{ obs}=\dfrac{\overline{x}-\mu_{0}}{\frac{s}{\sqrt{n}}}=\dfrac{7.37-7}{\frac{0.82}{\sqrt{35}}}=2.693$

$t_{1-\alpha}=qt(1-0.05, df=34)=1.69$, valor crítico (área a la izquierda del valor umbral 95%)

Se cumple $t_{obs}>t_{1-\alpha}$

Explicación:
Si la hipótesis nula fuese cierta, lo normal sería encontrar valores alrededor del valor central de esta hipótesis nula (en nuestro caso, 7). Si encontramos valores suficientemente grandes, podemos concluir que esta hipótesis nula no sea cierta. Para ello nos basamos en el nivel de confianza (y significancia).

Como el valor observado es mayor que el crítico, podemos rechazar la hipótesis nula.

### 5.2. Calcular el estadístico de contraste y el valor p
El valor p es la probabilidad de que, asumiendo que H0 sea cierta, observemos valores iguales o más extremos que t_obs. Si esta probabilidad es inferior a alfa, entonces podemos rechazar H0.

$t_{ obs}=\dfrac{\overline{x}-\mu_{0}}{\frac{s}{\sqrt{n}}}=\dfrac{7.37-7}{\frac{0.82}{\sqrt{35}}}=2.693$

$p=pt(tobs, df=n-1, lower.tail=FALSE)=pt(2.693,df=34,lower.tail=FALSE)=0.00545$, usamos lower.tail=FALSE para que calcule solo el área a la derecha del valor observado.

Se cumple que $p<\alpha$, por lo tanto se rechaza la hipótesis nula.

### 6.  Interpretar los resultados
Comparando el valor observado con el valor crítico, se rechaza la hipótesis nula puesto que $t_{obs}=2,693>1.69$

A partir del valor $p$, se rechaza la hipótesis nula puesto que el valor $p=0.0545<0.05$.

### 7. Responder la pregunta de investigación
Con un nivel de confianza del 95%, se concluye que existe evidencia estadística significativa de que la media poblacional de horas de sueño en los adolescentes es mayor que 7 horas diarias.

Se concluye que existe evidencia estadísticamente significativa de que la media poblacional de horas de sueño en los adolescentes es mayor que 7 horas diarias ($p<0.01$).



## Caso de uso: Contraste de dos muestras.
### 1. Formular la pregunta o hipótesis de investigación
¿las mujeres duermen un promedio de horas diarias diferente a las de los hombres?

### 2. Escribir las hipótesis estadísticas
$H_0:\mu_1 = \mu_2$
$H_1:\mu_1 \neq \mu_2$

### 3. Recoger y medir los datos de la muestra
$\overline{x_1}=7.38$   /   $\overline{x_2}=7.71$ 
$s_1=0.84$   /   $s_2=0.83$
$n_1=35$   /   $n_2=33$

### 4. Estadístico de contraste
Test (bilateral, dada la hipótesis alternativa) sobre la media **de dos muestras independientes** asumiendo que las poblaciones siguen una distribución normal  con varianzas desconocidas (iguales).

Asumimos que las poblaciones siguen una distribución normal aplicando el Teorema del Límite Central. Puesto que el tamaño de la población es suficientemente grande (n>30) podemos asumir que la distribución de las medias muestrales tiende a seguir una distribución normal. Esto nos permite aplicar métodos estadísticos basados en la normalidad incluso cuando la población no sigue esa distribución.

Respecto a las varianzas poblacionales desconocidas. Podemos estimar las varianzas poblacionales a partir de las varianzas muestrales y, por tanto, aplicar la distribución t de Student. Hay que realizar un test de contraste para saber si las varianzas son iguales o diferentes.

Bajo la hipótesis nula, el estadístico de contraste $t_{obs}$ sigue una distribución t de Student con $n_1 + n_2 - 2$ grados de libertad:

$t_{ obs}=\dfrac{\overline{x_1}-\overline{x_2}}{s\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}\sim t_{n_1+n_2-2}$

$S=\sqrt{\frac{(n_1-1)s^2_1+(n_2-1)s^2_2}{n_1+n_2-2}}$

donde $S$ es el valor de varianza común.

### 5. Calcular el estadístico de contraste y el valor crítico
Hipótesis alternativa: $H_1:\mu_1 \neq \mu_2$

Rechazo de la hipótesis nula si:
$|t_{obs}|>t_{1-\frac{\alpha}{2}}$
$p<\alpha$

![[Pasted image 20260411132130.png]]

$t_{obs}=-1.66$
$df=n_1+n_2-2=66$

Nivel de confianza: 95%
Nivel de significancia: $\alpha=0.05$

$t_{1-\frac{\alpha}{2}}=1.997$
$t_{\frac{\alpha}{2}}=-1.997$

No se cumple $|t_{obs}|>t_{1-\frac{\alpha}{2}}$. $t_{obs}$ está en la zona de aceptación. ==No se puede rechazar la hipótesis nula.==


$p=pt(abs(-1.66), df=66, lower.tail=FALSE) * 2=0.102$
No se cumple que $p< \alpha$, por lo que ==no se puede rechazar la hipótesis nula==.

### 6. Interpretar los resultados.
Comparando el valor observado con el valor crítico, no se puede rechazar la hipótses nula puesto que $|t_{bos}|=1.66$ está en la zona de aceptación (valor crítico 1.997).

A partir del valor $p$, no se puede rechazar la hipótesis nula puesto que el valor $p=0.102$ no es menor que 0.05.

### 7. Responder la pregunta de investigación
Con un nivel de confianza de 95%, no se puede concluir que las horas de sueño promedio de mujeres y hombres sean diferentes.

O

No se ha encontrado evidencia suficiente para concluir que las horas de sueño promedio entre mujeres y hombres sean diferentes ($p=0.102$).

## References

## Related notes