# Comparacion con repos previos pre-IA generativa

## Idea principal

Este dataset ya fue trabajado muchas veces antes de la era de IA generativa. Eso es bueno para el proyecto, porque permite comparar si nuestros resultados estan en un rango razonable.

La conclusion corta es esta:

> Nuestro resultado no es raro. La readmision a 30 dias es dificil de predecir con este dataset. Varios trabajos previos tambien obtienen AUC modestos, cerca de 0.63 a 0.66. La diferencia de nuestro proyecto es que no solo busca "ganar" con un modelo, sino explicar readmision, recurrencia y estancia con modelos interpretables.

## Criterio de busqueda

Se buscaron repositorios y proyectos que usaran el dataset conocido como:

- `Diabetes 130-US hospitals for years 1999-2008`
- `diabetic_data.csv`
- readmision hospitalaria de pacientes diabeticos

Para llamar a un trabajo "pre-IA generativa" se uso un criterio practico: repositorios creados o trabajados antes de noviembre de 2022, cuando ChatGPT todavia no era una herramienta comun de apoyo para programar o escribir proyectos.

## Fuentes revisadas

| Fuente | Fecha verificada | Enfoque | Modelos usados | Resultado relevante |
| --- | --- | --- | --- | --- |
| [angelmanzur/Diabetes_130Hospitals](https://github.com/angelmanzur/Diabetes_130Hospitals) | creado en 2019 | Entender variables relacionadas con `readmitted` | Gradient Boosting, Decision Tree, Random Forest | AUC bajo, aprox. 0.54 a 0.55. El propio repo concluye que los modelos predicen poco. |
| [brunoarine/diabetes](https://github.com/brunoarine/diabetes) | creado en 2021 | Predecir readmision temprana | Logistic Regression, Random Forest, XGBoost | AUC alrededor de 0.63 a 0.66. El mejor desempeno no es alto. |
| [uncanny-valley/diabetes-readmission](https://github.com/uncanny-valley/diabetes-readmission) | creado en 2021 | Clasificacion binaria de readmision antes de 30 dias | Logistic Regression, Decision Tree, KNN, Random Forest, XGBoost, AdaBoost, Bagging | AUC alrededor de 0.65 en validacion. |
| [WHaMoCaTY/Diabetes-130-UShospitals](https://github.com/WHaMoCaTY/Diabetes-130-UShospitals) | creado en 2019 | Proyecto de curso sobre el mismo dataset | Logistic Regression, Random Forest, SVM, redes neuronales, clustering | Trabaja una version multiclase y reporta accuracy, por eso no se compara directo con nuestro AUC. |
| [Proyecto de Xiaojue Zhou](https://zhouxiaojue.github.io/project/diabetesprediction/) | portafolio de proyecto anterior a la era IA generativa | Prediccion de readmision y segmentacion de pacientes | Clasificacion, importancia de variables y clustering | Coincide en que el proyecto combina limpieza, EDA, modelos y explicacion de factores. |
| [BMC Medical Informatics and Decision Making, 2021](https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-021-01423-y) | publicado en 2021 | Comparacion academica de metodos ML para readmision | Random Forest, Decision Tree, SVM, redes neuronales y otros | Sirve como referencia externa: el problema es conocido y se ha abordado con varios modelos ML. |

Tambien se revisaron las fuentes base del dataset:

- [UCI Machine Learning Repository: Diabetes 130-US hospitals](https://archive.ics.uci.edu/dataset/296/diabetes+130+us+hospitals+for+years+1999+2008)
- [Kaggle: Diabetes 130-US hospitals for years 1999-2008](https://www.kaggle.com/datasets/brandao/diabetes)

## Comparacion contra nuestro proyecto

| Aspecto | Trabajos previos | Nuestro proyecto unificado |
| --- | --- | --- |
| Pregunta principal | Casi siempre: predecir readmision menor a 30 dias | Explicar readmision, recurrencia y duracion de estancia |
| Unidad de analisis | A veces usan admisiones completas; a veces pacientes unicos | Version final usa pacientes unicos para mejorar independencia |
| Limpieza | Eliminan columnas con faltantes y recodifican categorias | Hace lo mismo, pero lo explica con lenguaje mas sencillo |
| Modelos | Mucho enfoque en comparar modelos predictivos | Usa modelos interpretables: logistica, Binomial Negativa y Gamma |
| Desempeno | AUC usualmente modesto, aprox. 0.63 a 0.66 cuando la tarea es binaria | AUC 0.608 en la version final limpia |
| Interpretacion | Algunos repos se enfocan mas en metricas | El reporte traduce resultados a decisiones hospitalarias |
| Graficas | Varian mucho; algunas son tecnicas | Se dejaron solo graficas importantes en el reporte y todas visibles en VS Code |

## Que aprendemos de la comparacion

Primero, el AUC de nuestro modelo no debe presentarse como un fracaso. Debe presentarse con honestidad: la readmision temprana es dificil de predecir solo con variables administrativas. Otros trabajos con modelos mas complejos tambien reportan resultados moderados.

Segundo, no conviene prometer "prediccion perfecta". Es mejor decir que el modelo ayuda a identificar senales de riesgo. La senal mas fuerte en nuestro proyecto es el uso previo del hospital: ingresos previos, urgencias previas y complejidad clinica.

Tercero, nuestro proyecto tiene una ventaja para una presentacion de curso: explica tres fenomenos relacionados, no solo uno. La readmision es una respuesta binaria, la recurrencia es un conteo y la estancia es una variable positiva con sesgo a la derecha. Por eso tiene sentido usar tres familias de modelos.

## Como decirlo en la presentacion

Una forma sencilla de explicarlo:

> Como este dataset es publico y muy usado, revisamos trabajos anteriores a la era de IA generativa. Encontramos que muchos intentan predecir readmision con Random Forest, XGBoost o regresion logistica. Sus AUC suelen ser moderados. Eso confirma que el problema no es trivial. Nuestro enfoque no busca vender una prediccion perfecta, sino entender que variables concentran riesgo y como eso puede apoyar decisiones del hospital.

## Como decirlo en el reporte

Una frase util para el reporte:

> La revision de trabajos previos muestra que este dataset suele producir desempenos predictivos moderados. Por eso, el valor principal del proyecto no esta en afirmar que el modelo predice perfectamente, sino en usar modelos interpretables para explicar patrones de uso hospitalario y convertirlos en recomendaciones operativas.

## Decision para nuestra version final

No vamos a cambiar el proyecto para copiar los repos previos. La mejor decision es mantener la version neutral actual:

- usar modelos simples e interpretables;
- mencionar que modelos mas complejos existen, pero no resuelven completamente el problema;
- defender que el proyecto esta orientado a explicacion y toma de decisiones;
- usar la comparacion como respaldo en la presentacion y en la discusion de limitaciones.
