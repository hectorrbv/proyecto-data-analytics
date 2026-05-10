# Proyecto Final: Readmisiones, Recurrencia y Estancia Hospitalaria

## Resumen Ejecutivo

Este proyecto estudia a pacientes con diabetes para responder tres preguntas:

1. ¿Qué factores se relacionan con una readmisión en menos de 30 días?
2. ¿Qué factores se relacionan con más admisiones hospitalarias previas?
3. ¿Qué factores se relacionan con estancias más largas?

El trabajo siguió la lógica vista en clase:

1. revisar la calidad del dato
2. hacer análisis exploratorio
3. validar patrones con pruebas estadísticas
4. usar modelos simples e interpretables

La idea principal es esta: el problema del hospital no es uno solo. La readmisión a 30 días, la recurrencia hospitalaria y la duración de la estancia están conectadas, pero no son lo mismo. Por eso conviene analizarlas con herramientas distintas.

## 1. Problema de negocio

Las readmisiones no planeadas dañan al paciente y también presionan la operación del hospital. Además, cuando un paciente entra varias veces o se queda más tiempo del esperado, se ocupan camas, recursos y personal.

Por eso el proyecto se enfoca en tres metas:

1. detectar señales de mayor riesgo de readmisión
2. entender qué caracteriza a los pacientes con más recurrencia
3. encontrar variables asociadas con estancias más largas

## 2. Datos

Se usó el archivo `diabetic_data.csv`.

Características generales:

- 101,766 registros
- pacientes con diabetes
- hospitales de Estados Unidos

Variables clave:

- `readmitted`
- `time_in_hospital`
- `number_inpatient`
- `num_medications`
- `num_lab_procedures`
- `number_diagnoses`
- `diabetesMed`
- `change`

## 3. Calidad del dato y preprocesamiento

Primero se revisó la calidad del dato.

Puntos importantes:

- varios campos usaban `"?"` para representar datos faltantes
- algunas variables tenían muchos faltantes, por ejemplo `weight`, `medical_specialty` y `payer_code`
- no era buena idea borrar filas de forma agresiva porque se perdía mucha información

Decisiones principales:

1. convertir `"?"` en `NaN`
2. sacar identificadores como `encounter_id` y `patient_nbr` del modelado
3. crear la variable `readmit_30`, donde `1` significa readmisión en menos de 30 días
4. conservar la ausencia de datos como parte del diagnóstico, en vez de esconderla

La idea que debes decir al presentar es:

"No limpiamos por limpiar. Cada decisión de preprocesamiento se hizo para no distorsionar el análisis."

## 4. Análisis exploratorio

El análisis exploratorio mostró tres cosas importantes.

### 4.1 La estancia no es una variable simétrica

`time_in_hospital` es positiva y está cargada hacia la derecha. Eso quiere decir que la mayoría de las estancias son relativamente cortas, pero hay un grupo de pacientes que se queda mucho más tiempo.

### 4.2 La recurrencia es un conteo con sobredispersión

`number_inpatient` tiene muchos ceros y una cola larga. Además, su varianza es claramente mayor que su media. Eso es importante porque avisa que un modelo Poisson simple puede quedarse corto.

### 4.3 La readmisión cambia entre grupos

Se observaron diferencias por:

- edad
- uso de medicamento para diabetes
- cambio de medicación
- variables de uso previo del hospital

La idea que debes decir al presentar es:

"El EDA no solo sirvió para hacer gráficas. Sirvió para ver qué forma tienen los datos y qué tipo de modelo tiene sentido usar después."

## 5. Inferencia estadística

Después del EDA, se hicieron pruebas para confirmar si los patrones visuales podían sostenerse con evidencia estadística.

Se usaron:

- Shapiro-Wilk para revisar normalidad
- Levene para revisar varianzas
- Mann-Whitney y Kolmogorov-Smirnov para comparar distribuciones
- Chi-cuadrada para variables categóricas

### Conclusión simple de esta parte

1. Las variables principales de uso hospitalario no se comportan como variables normales limpias.
2. Eso justifica usar pruebas robustas o no paramétricas.
3. Algunas variables demográficas y de tratamiento sí muestran asociación estadística con la readmisión.

La frase simple aquí es:

"Primero vimos diferencias en las gráficas. Luego usamos inferencia para confirmar que esas diferencias no parecen ser puro ruido."

## 6. Modelos e interpretación simple

## 6.1 Modelo de readmisión a 30 días

Se usó un **GLM binomial** porque la variable respuesta es binaria.

Resultado general:

- AUC aproximada: `0.64`
- accuracy aproximada: `0.889`

Esto no significa que el modelo sea excelente para predecir. Significa que sí sirve para entender dirección y fuerza de algunas asociaciones.

### Lectura simple de coeficientes

Hallazgos más útiles:

1. `number_inpatient` fue una de las señales más fuertes.
   Traducción simple:
   "Los pacientes con más admisiones previas tienen más riesgo de volver a entrar en menos de 30 días."
   Lectura rápida del coeficiente:
   "En el modelo, una admisión previa adicional se asoció con un aumento de alrededor de 31% en las odds de readmisión."

2. `diabetesMed = Yes` también se relacionó con mayor readmisión.
   Traducción simple:
   "Recibir medicamento para diabetes parece marcar pacientes más complejos o más vigilados clínicamente."
   Lectura rápida del coeficiente:
   "Esta categoría se asoció con alrededor de 18% más odds de readmisión."

3. Más diagnósticos, más visitas previas a urgencias y más días en el hospital también se relacionaron con mayor riesgo.
   Traducción simple:
   "Cuando el caso clínico se ve más complejo o el paciente ya venía usando más el hospital, la probabilidad de readmisión sube."
   Lectura rápida del coeficiente:
   "Cada diagnóstico adicional se asoció con cerca de 4% más odds, cada visita previa a urgencias con cerca de 4% más odds, y cada día extra de estancia con cerca de 2% más odds."

### Qué conviene decir

"Este modelo no busca adivinar perfecto quién regresa. Busca mostrar qué señales acompañan a los pacientes con mayor riesgo de readmisión."

## 6.2 Modelo de recurrencia hospitalaria

Se comparó un **Poisson** contra una **Binomial Negativa**.

Resultado general:

- Poisson quedó un poco mejor en error simple de prueba
- Binomial Negativa tuvo un AIC mucho menor
- el parámetro `alpha` fue cercano a `1.56`

### Interpretación simple

La conclusión importante no es cuál gana por muy poco en una sola métrica. La conclusión importante es esta:

"La recurrencia no se comporta como un conteo parejo. Hay más variación de la que Poisson espera."

Hallazgos más útiles:

1. Las visitas previas a urgencias fueron la señal más fuerte.
   Traducción simple:
   "Quien ya venía usando urgencias con frecuencia tiende a concentrar más recurrencia hospitalaria."
   Lectura rápida del coeficiente:
   "Fue el efecto más fuerte del modelo, incluso después de transformar la variable para estabilizar la escala."

2. También importaron las visitas ambulatorias previas.
   Traducción simple:
   "La recurrencia no aparece de la nada; suele venir acompañada de uso previo del sistema."
   Lectura rápida del coeficiente:
   "Esto refuerza la idea de que la recurrencia es parte de una historia previa de uso hospitalario."

3. Más días de estancia y más medicamentos también se relacionaron con más recurrencia.
   Traducción simple:
   "Los pacientes más complejos y con mayor carga de atención tienden a regresar más veces."
   Lectura rápida del coeficiente:
   "La señal general del modelo es clara: a mayor complejidad y mayor uso previo, mayor recurrencia esperada."

### Qué conviene decir

"Poisson sirve como punto de partida, pero la binomial negativa cuenta mejor la historia del dato: unos pocos pacientes concentran mucha más recurrencia de la esperada."

## 6.3 Modelo de duración de estancia

Se usó un **GLM Gamma con enlace log** porque `time_in_hospital` es positiva y sesgada a la derecha.

Resultado general:

- RMSE aproximado: `2.59`
- MAE aproximado: `1.94`

### Interpretación simple

Hallazgos más útiles:

1. Más diagnósticos se relacionaron con estancias más largas.
   Traducción simple:
   "Cuando el paciente llega con un cuadro más complejo, tiende a quedarse más tiempo."
   Lectura rápida del coeficiente:
   "Cada diagnóstico adicional se asoció con un aumento cercano a 3% en la estancia esperada."

2. Más admisiones previas también se relacionaron con estancias más largas.
   Traducción simple:
   "Los pacientes con historia hospitalaria más pesada no solo regresan más; también tienden a ocupar cama por más tiempo."
   Lectura rápida del coeficiente:
   "Cada admisión previa adicional se asoció con cerca de 3% más duración esperada."

3. Más medicamentos se relacionaron con estancias más largas.
   Traducción simple:
   "Una mayor carga de tratamiento suele venir con estancias más largas."
   Lectura rápida del coeficiente:
   "Cada medicamento adicional se asoció con un aumento cercano a 3% en la estancia esperada."

### Qué conviene decir

"Gamma fue una buena elección porque respeta la forma real de la variable: días positivos y distribución sesgada."

## 7. Recomendaciones para el hospital

Con base en el análisis, las recomendaciones más defendibles son:

1. Dar seguimiento más fuerte al alta de pacientes con más uso previo del hospital.
2. Tratar la recurrencia como un problema concentrado en ciertos perfiles, no como un patrón uniforme.
3. Usar señales de complejidad clínica, como más diagnósticos y más medicamentos, para anticipar readmisión y estancias largas.

En lenguaje simple:

"El hospital gana más si identifica mejor a los pacientes complejos antes de que regresen, en lugar de tratar igual a todos."

## 8. Limitaciones

Es importante decir esto con claridad:

1. El análisis muestra asociación, no causalidad.
2. Hay variables con faltantes importantes.
3. El dataset es administrativo y tiene límites de registro.
4. El análisis está a nivel de encuentros hospitalarios, no de toda la historia clínica completa de cada paciente.

## 9. Cierre

La conclusión final puede decirse así:

"El proyecto muestra que la readmisión, la recurrencia y la estancia larga comparten señales de complejidad clínica y uso previo del hospital. Sin embargo, cada fenómeno tiene su propia forma estadística, y por eso cada uno necesita un enfoque analítico distinto."
