## Enunciado
El nuevo Chief Data Officer se incorpora a la organización en uno de los momentos más
críticos de su historia reciente. El escaso crecimiento orgánico, las elevadas necesidades de
inversión, la intensa presión regulatoria, la pérdida de confianza de los inversores y un alto
nivel de endeudamiento han erosionado significativamente la credibilidad de la compañía
ante los mercados.
En este contexto, el CDO ha decidido incorporar a vuestro equipo como parte del Data
Office. Las decisiones que adopte el equipo (basadas en el temario de la asignatura) serán
determinantes para definir el futuro de la empresa: aprovechar el potencial estratégico de
los datos como palanca de recuperación o, por el contrario, agravar la crisis mediante una
gestión ineficiente de la información.

## Reto 1
Es vuestro primer día en la organización y el panorama es preocupante. Existe una cantidad
ingente y desordenada de archivos Excel que recogen la actividad de los distintos
departamentos sin criterios comunes ni trazabilidad. Además, la empresa dispone de una
base de datos operativa carente de documentación, lo que dificulta su explotación analítica.
En este contexto, el CEO solicita con carácter urgente un informe de predicción de ventas
que deberá presentarse ante la junta de accionistas en el plazo de una semana.
Desafío:
¿Qué acciones priorizaríais ante esta situación? ¿Qué decisiones tomaríais y cuál sería el
resultado esperado del reto?

## Pensamientos

Chief data officer
Responsable de todas las iniciativas de explotación de datos vinculadas a la data science. Debe tener responsabilidad directiva y desempeñar el papel de agente del cambio dentro de la organización.

Dilema:
El jefe nos pide un informe de ventas en una semana, pero no tenemos ninguna estructura para ello.

¿Priorizamos informe?¿Cómo lo hacemos?
Intentamos centrarnos en la estructura?

## Respuestas de compañeros
- **Jessica**: 
	- No utilizar IA pa meterle pecha de datos, ya que no va a dar buenos resultados
	- Propone clasificar y ordenar toda la info y crear el informe más tarde
	- Respuesta de **Santiago**:
		- Hace un road map de que hacer esta semana
		- 1. Acciones correctivas inmediatas: limpiar, transformar, etc.
		- 2. Entrenar modelos predictivos para generar el informe.
		- 3. Realizar acciones preventivas una vez pasada la tormenta.
	  Respuesta de **Gonzalo**:
		- Cree que no da tiempo para el plan de Santiago en 7 días
		- Quiere desarrollar un MVP para esta semana.
- **Diego Manuel**:
	- Habla sobre los conjuntos de origen de los datos.
	- No cometer acciones aisladas dentro de los TIC, sino comunicarnos con el resto de la compañía.
	- Propone un modelo ETL, un datamart, etc etc. Mucho tiempo.
	- Respuesta **Gonzalo**:
		- Responde que construir el DataMart es demasiado tiempo.


## Respuesta hilo Diego Manuel
Buenas equipo. El planteamiento de Diego me parece muy buena idea, pero coincido con Gonzalo, no tenemos tiempo en una semana de llevar a cabo tal transformación. Analizando la situación, no tenemos el tiempo ni el capital de implantar un proyecto analítico en una semana. Por lo que opto por la idea de Gonzalo de un MVP. 

Yo priorizaría hablar con los encargados de los departamentos pertinentes (ventas, entiendo) para que nos expliquen ellos cómo recaban y gestionan los datos, qué pausas utilizan (si alguna) y qué medios (excel, base de datos o ambos).

## Abro hilo imposibilidad de realizar la tarea
Buenas equipo,
El plan propuesto por Gonzalo de llevar a cabo un MVP para sacar las castañas del fuego al CEO me parece la idea más adecuada (teniendo en cuenta el tiempo que tenemos). Sin embargo, yo propongo otra opción, puede que descabellada: explicarle al CEO, con franqueza, que lo que pide es imposible.

Partiendo del modelo de madurez DELTTA de Davenport, Harris y Morison (explicado en el tema de Organizaciones orientadas a datos), nuestra organización se encuentra en casi todos los apartados en la fase 1: **Incapacidad analítica**. La organización no está capacitada de ninguna manera para implantar un proyecto analítico de predicción de ventas **en una semana**. Temo que si intentamos llevar a cabo el proyecto en este margen de tiempo, no vamos a poder garantizar unos buenos resultados.

Mi propuesta es:
1. El CEO ha tenido reuniones con inversores antes de nuestra llegada. Para esta ocasión, tendrá que utilizar las herramientas de las que disponía en las anteriores ocasiones. Podemos dedicar parte del equipo a ayudarle recopilar y limpiar datos y que realice alguna predicción en base a modelos de regresión lineal en excel.
2. Comenzar con el proceso de transformación a una organización orientada al dato. Utilizando el modelo DELTTA, analizar en qué fase está la organización para cada factor y trabajar para mejorarlos. Por ejemplo, estandarizar los datos que se generan en la empresa, crear un data warehouse, hacer limpieza de todos los datos que la empresa tiene actualmente, etc.
3. Comenzar a implantar una cultura de orientación al dato en la organización. Analizar cómo trabajan los distintos departamentos de la organización y realizar talleres para enseñarles las buenas prácticas a la hora de trabajar con los datos. Como se explica en *Organizaciones orientadas al dato*, uno de los primeros pasos debe ser cambiar la actitud, hábitos y conocimientos de los usuarios de negocio para que nuestra labor sea luego más sencilla y eficaz.