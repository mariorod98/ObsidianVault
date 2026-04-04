Buenas compañeros, me excuso yo también por el retraso en mi respuesta. 
Me parece que tenemos bastante bien definido el plan de acción en 3 fases, de la más directa e inmediata hacia el mantenimiento a futuro.

Creo que lo único que queda es definir más concretamente el sistema de IA Explicable propuesto por @Gonzalo Sánchez López. Es de vital importancia que nuestra IA deje de ser una *caja negra* ya que la normativa europea *AI ACT* [1] indica, en su Artículo 13, que todo algoritmo IA de alto riesgo (como el nuestro) debe tener suficiente transparencia para explicar el proceso.

Hay dos  consideraciones a tener en cuenta, definidas en _Ética en la ciencia de datos_ [2]:
- Requerimos de un sistema que sea capaz de dar varios niveles de **interpretabilidad**. Por un lado, que muestre qué variables del dataset han tenido más peso en la toma de decisión para que así el médico pueda identificar qué se ha tenido en cuenta y determine si es correcta la asunción o no. Por el otro lado, necesitamos una explicación más granular para nuestro equipo que nos permita trazar el proceso de razonamiento desde el input hasta el output.
- Sin embargo, la interpretabilidad tiene un coste. Generalmente, **a mayor interpretabilidad menor precisión** tendrá el algoritmo, ya que un modelo explicable está más restringido y es, por lo tanto, menos precisa. ¿Cuánta precisión estamos dispuestos a perder por tener un algoritmo más entendible?

**Propuesta**
Propongo, durante la fase 2 de nuestro plan, implementar la IA Explicable tipo *post-hoc*. De este modo, nuestro algoritmo generará una predicción a partir de los datos y la IA Explicable se ejecutará después de la toma de decisión para explicar cómo ha sido. Específicamente, el modelo SHAP es un candidato ideal para nuestras necesidades, y ya ha sido implementado en diversos contextos hospitalarios para cumplir el mismo objetivo. [3] [4]



[1] Regulation (EU) 2024/1689 of the European Parliament and of the Council of 13 June 2024 laying down harmonised rules on artificial intelligence and amending Regulations (EC) No 300/2008, (EU) No 167/2013, (EU) No 168/2013, (EU) 2018/858, (EU) 2018/1139 and (EU) 2019/2144 and Directives 2014/90/EU, (EU) 2016/797 and (EU) 2020/1828 (Artificial Intelligence Act), OJ L, 2024/1689, 12.7.2024.http://data.europa.eu/eli/reg/2024/1689/oj

[2] Pita Lozano, A. (2025). _Ética en la ciencia de datos_. Universitat Oberta de Catalunya (UOC).

[3] Rui Fa et al., Prediction of prolonged length of stay from first 2 days of hospitalization data: a SHAP value-based variable selection method for a simplified model, _International Journal for Quality in Health Care_, Volume 37, Issue 4, October 2025, mzaf116,https://doi.org/10.1093/intqhc/mzaf116

[4] Wei J, Cao H, Peng M, Zhang Y, Li S, et al. (2025) An interpretable machine learning model for predicting in-hospital mortality in ICU patients with ventilator-associated pneumonia. PLOS ONE 20(1): e0316526. https://doi.org/10.1371/journal.pone.0316526