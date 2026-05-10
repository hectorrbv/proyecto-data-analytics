# Reportes completos revisados sobre el mismo dataset

## Para que sirve esta revision

Esta nota complementa la comparacion con repos antiguos. Aqui no importa si el trabajo es reciente o si ya pertenece a la era de IA generativa. El objetivo es encontrar reportes completos para comparar estructura, profundidad, metricas y forma de explicar resultados.

La conclusion corta:

> Los reportes mas completos no solo entrenan modelos. Tambien explican limpieza, desbalance, validacion, interpretabilidad, limitaciones y uso operativo. Nuestro proyecto ya cubre buena parte de eso, pero puede mejorar si usamos algunos elementos de estos reportes como referencia para explicar mejor la comparacion externa.

## Reportes mas utiles

| Prioridad | Fuente | Tipo | Que tiene de completo | Que podemos tomar |
| --- | --- | --- | --- | --- |
| 1 | [GSU Data Mining Project](https://arrdel.github.io/patient-readmission-prediction/) | Proyecto academico con reporte, codigo y slides | Pipeline completo, SMOTE, validacion cruzada, ROC, PR-AUC, interpretacion y discusion | Muy buen modelo para la presentacion: claro, visual y honesto con metricas modestas |
| 2 | [Cureus 2025: Predicting 30-Day Hospital Readmission](https://pubmed.ncbi.nlm.nih.gov/40385730/) | Articulo academico abierto | Compara logistica, Random Forest, XGBoost y DNN; usa SHAP; reporta AUC claros | Excelente benchmark numerico: XGBoost 0.667, logistica 0.642, RF 0.630 |
| 3 | [BMC 2021: 30-days readmission risk](https://link.springer.com/article/10.1186/s12911-021-01423-y) | Articulo academico abierto | Describe dataset, limpieza, balanceo, seleccion de 23 factores, modelos y limitaciones | Muy util para justificar que edad, admisiones previas, urgencias y diagnosticos importan |
| 4 | [JMAI 2024: Comparison of ML models](https://jmai.amegroups.org/article/view/9179/html) | Articulo academico abierto | Compara 10 modelos ML y LSTM, usa SMOTE, group k-fold y Grey Wolf Optimizer | Sirve para discutir que RF/XGBoost suelen ganar, pero requieren mas complejidad |
| 5 | [Yung Chou: Data Preparation of Diabetes Dataset](https://yungchou.github.io/site/) | Reporte tecnico de preparacion | Muy detallado en limpieza, pacientes unicos, imputacion, diagnosticos y feature selection | Muy util para defender decisiones de limpieza y explicar por que usar pacientes unicos |
| 6 | [AWS SageMaker Pipeline](https://aws.amazon.com/blogs/publicsector/predict-diabetic-patient-readmission-using-multi-model-training-amazon-sagemaker-pipelines/) | Tutorial tecnico industrial | Pipeline de despliegue, entrenamiento y arquitectura con SageMaker | Sirve como referencia de como se veria un siguiente paso productivo |
| 7 | [MDPI Future Internet 2023: Hybrid Deep Model](https://www.mdpi.com/1999-5903/15/9/304) | Articulo con deep learning | Predice readmision y estancia; usa CNN 1D, algoritmo genetico, balanceo y validacion | Sirve como contraste: muy tecnico y con metricas muy altas, menos facil de explicar |
| 8 | [ScienceDirect / CMES 2025](https://www.sciencedirect.com/org/science/article/pii/S1526149225000724) | Articulo reciente | Predice readmision y estancia; reporta pipeline, balanceo, validacion y Random Forest | Sirve como comparacion reciente, pero sus metricas altas deben tratarse con cuidado |
| 9 | [ResearchGate 2023: Big Data Analytics](https://www.researchgate.net/publication/375690075_Implementation_of_Big_Data_Analytics_on_Diabetes_130-US_Hospitals_for_year_1999-2008_for_predicting_patient_readmission) | Preprint/reporte tecnico | Usa Hadoop, PySpark, logistica, decision tree y Random Forest | Util para ver estructura de reporte, pero sus resultados perfectos sugieren posible sobreajuste |
| 10 | [arXiv 2024: LSTM vs modelos tradicionales](https://arxiv.org/abs/2406.19980) | Preprint academico | Compara XGBoost, LightGBM, CatBoost, Decision Tree, RF y LSTM; usa SHAP | Util para mencionar que modelos complejos pueden sobreajustar si no se validan bien |

## Benchmark numerico cuidadoso

No todos los numeros se pueden comparar directamente. Cada reporte define el target, el balanceo y la validacion de forma distinta.

| Fuente | Mejor resultado reportado | Comentario |
| --- | ---: | --- |
| Nuestro proyecto unificado | AUC 0.608 | Modelo limpio, interpretable y con pacientes unicos |
| GSU Data Mining Project | XGBoost ROC AUC 0.62 | Muy comparable porque tambien reconoce que el problema es dificil |
| Cureus 2025 | XGBoost AUC 0.667; logistica 0.642 | Buen punto de referencia externo |
| BMC 2021 | RF con mejor AUC entre modelos | No siempre reporta el numero visible en resumen, pero identifica RF como mejor |
| JMAI 2024 | RF/XGBoost accuracy 0.88 aprox. | Mas dificil de comparar por SMOTE, GWO y F1 como metrica principal |
| MDPI 2023 | accuracy aprox. 97% | No lo usaria como comparacion directa; puede depender de balanceo, definicion de clases y arquitectura |
| ResearchGate 2023 | RF con AUC/accuracy perfectos | No lo usaria como benchmark fuerte; hasta el mismo texto menciona posible overfitting |

## Que reportes conviene citar en nuestro escrito

Si hay poco espacio, yo citaria solo tres:

1. GSU Data Mining Project, porque esta muy cerca del estilo de curso y tiene reporte, codigo y slides.
2. Cureus 2025, porque da numeros claros y recientes: XGBoost 0.667, logistica 0.642, RF 0.630.
3. BMC 2021, porque es un articulo abierto y explica bien factores de riesgo como admisiones previas, edad, urgencias y diagnosticos.

Si queremos defender limpieza y preparacion de datos, tambien conviene citar Yung Chou, porque muestra con detalle decisiones parecidas a las nuestras: quitar pacientes repetidos, agrupar diagnosticos y eliminar variables con demasiados faltantes.

## Que elementos podemos copiar como estructura, no como contenido

De los reportes completos, lo mas valioso para nuestro proyecto es esta estructura:

1. Problema de negocio: por que importa la readmision.
2. Dataset: origen, tamano, variables principales y limitaciones.
3. Limpieza: valores faltantes, pacientes repetidos, diagnosticos y target.
4. EDA: distribucion de readmision, edad, estancia, uso hospitalario.
5. Modelos: uno interpretable y, si se quiere, uno mas flexible como benchmark.
6. Validacion: train/test, AUC, matriz de confusion o sensibilidad/especificidad.
7. Interpretacion: odds ratios, feature importance o SHAP.
8. Recomendaciones: que haria el hospital con esto.
9. Limitaciones: datos viejos, faltantes, no causalidad, falta de variables sociales.
10. Siguientes pasos: calibracion, validacion externa, fairness y despliegue.

Nuestro reporte ya tiene casi todo, excepto una comparacion numerica externa mas explicita y una pequena nota sobre calibracion/fairness como trabajo futuro.

## Mensaje fuerte para la presentacion

Una frase sencilla:

> Revisamos reportes completos del mismo dataset. Los mejores trabajos no prometen prediccion perfecta; explican que la readmision es dificil, comparan modelos y luego traducen resultados a decisiones. Nuestro proyecto sigue esa idea: prioriza explicacion, limpieza clara y recomendaciones operativas.

Otra frase para defender el AUC:

> Aunque algunos reportes recientes muestran metricas muy altas, los trabajos mas comparables reportan AUC cercanos a 0.62-0.67. Nuestro AUC de 0.608 esta por debajo, pero en el mismo orden de dificultad. Ademas, usamos un modelo interpretable y una muestra mas limpia de pacientes unicos.

## Que no conviene decir

No conviene decir:

> Nuestro modelo es el mejor.

Tampoco conviene decir:

> Los reportes con 97% de accuracy prueban que el problema es facil.

Es mejor decir:

> Las metricas dependen mucho de la limpieza, el balanceo y la forma de validar. Por eso nuestro enfoque prioriza interpretabilidad y explicacion honesta.

## Recomendacion practica

Para el entregable final, no meteria todos estos reportes en el cuerpo principal. Los usaria asi:

- en el reporte: una frase corta en la seccion de trabajos previos;
- en la presentacion: una diapositiva de "benchmark externo";
- en preguntas y respuestas: usar Cureus, GSU y BMC para defender que el proyecto esta alineado con trabajos completos.
