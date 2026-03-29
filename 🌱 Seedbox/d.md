*El equipo de informática os entrega los datos para entrenar MediFutur. Provienen de tres fuentes diferentes: el historial antiguo en papel digitalizado (OCR), el actual sistema digital y datos de wearables (relojes inteligentes) cedidos por pacientes.*

*Al echar un primer vistazo, veis que los nombres están escritos en formatos diferentes ("Apellido, Nombre" vs. "Nombre Apellido"), hay campos vacíos en las edades y los wearables tienen datos duplicados. El jefe de cardiología tiene prisa por empezar las pruebas.*

Buenas equipo,

Por resumir todas las propuestas de este reto...



Respondiendo a las preguntas del reto:
**¿Qué acciones priorizaríais ante esta situación?**
1. Detener la ingesta de datos para poder definir un plan de mantenimiento adecuado y arreglar las inconsistencias entre las distintas fuentes de datos @Jessica Denise Sommer
2. Este proceso estará definido por las siguientes etapas @ Santiago Raymond Llorens:
	- **Identificar los responsables del proceso**: quien se encargará de cada subetapa de la limpieza y quién será responsable y coordinador del proceso.
	- **Definir un protocolo de calidad del dato**: Especificar qué estándares debe cumplir. Podemos
	- **Monitorizar la calidad del dato**:  Deberíamos garantizar que el dato mantiene estos estandares de calidad y que no surgen nuevas incompatibilidades al entrar nuevos datos. Para esto, creo que estaria bien tener unos indicadores de calidad, que sean cuantificables y se puedan evaluar a lo largo del tiempo.
	- **Informar**: Mantener actualizado a todo el equipo sobre la calidad del dato y las posibles mejoras implementadas, estado del monitoreo, etc.
**¿Qué decisiones tomaríais y cuál sería el resultado esperado del reto?**






Buenas equipo.

Respecto a la gobernanza del dato, me sumo a las propuestas de @José Rodríguez Sojo, @Iker Rodrigo Serrato Soteno y @José Rodríguez Sojo. Creo que es un programa de mantenimiento de la calidad del dato muy bien definido.

Más allá de la calidad del dato, creo deberíamos hablar también sobre otros aspectos del programa de gobierno del dato, aunque sea para plantear el diseño inicial de este programa.

En mi opinión, lo más importante es la necesidad de definir los **datos maestros** de nuestro sistema y de asegurar que su ciclo de vida es adecuado. Actualmente, los datos con los que trabajamos se encuentran en diferentes silos que nos dificulta trabajar con ellos. Desde el punto de vista de la gestión de datos maestros (CITA CICLO DE VIDA), deberíamos evitar la existencia de estos silos y centralizar todos los datos en un único data warehouse. De esta manera es más fácil asegurar su calidad y controlar su ciclo de vida y seguridad.

Como ya vamos a realizar el proceso de limpieza y de unificación de los datos para los que ya hay existentes, creo que deberíamos extender esto hacia un pipeline que, al recibir datos en estos silos, de forma automática los preprocese y almacene en el data warehouse. A futuro, puede ser interesante eliminar completamente los silos y que los datos captados se almacenen directamente en el data warehouse.
