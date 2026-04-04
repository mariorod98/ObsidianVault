Buenas compañeros, me excuso yo también por el retraso en mi respuesta. 
Me parece que tenemos bastante bien definido el plan de acción en 3 fases, de la más directa e inmediata hacia el mantenimiento a futuro.

Creo que lo único que queda es definir más concretamente el sistema de IA Explicable propuesto por @Gonzalo Sánchez López. Hay dos  consideraciones a tener en cuenta, definidas en (Pita Lozano, 2025):
- Requerimos de un sistema que sea capaz de dar varios niveles de **interpretabilidad**. Por un lado, que muestre qué variables del dataset han tenido más peso en la toma de decisión para que así el médico pueda identificar qué se ha tenido en cuenta y determine si es correcta la asunción o no. Por el otro lado, necesitamos una explicación más granular para nuestro equipo que nos permita trazar el proceso de razonamiento desde el input hasta el output.
- Sin embargo, la interpretabilidad tiene un coste. Generalmente, **a mayor interpretabilidad menor precisión** tendrá el algoritmo, ya que un modelo explicable está más restringido y es, por lo tanto, menos precisa. ¿Cuánta precisión estamos dispuestos a perder por tener un algoritmo más entendible?

**Propuesta**
Propongo, durante la fase 2 de nuestro plan, implementar la IA Explicable mediante método *post-hoc*, debido a la complejidad de nuestro sistema. Concretamente, 

[1] Pita Lozano, A. (2025). _Ética en la ciencia de datos_. Universitat Oberta de Catalunya (UOC).
[2] IBM (s.f.)¿Qué es la IA explicable? https://www.ibm.com/es-es/think/topics/explainable-ai