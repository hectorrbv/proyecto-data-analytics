# Guion Simple para la Presentación

## Diapositiva 1. Problema y objetivo

### Mensaje principal

El hospital quiere entender tres cosas:

1. quién tiene más riesgo de readmisión en menos de 30 días
2. quién tiende a regresar varias veces
3. quién tiende a quedarse más tiempo

### Frase simple para decir

"No vimos el proyecto como un solo problema. Lo vimos como tres problemas relacionados: readmisión, recurrencia y estancia."

## Diapositiva 2. Datos y método

### Mensaje principal

- 101,766 registros
- pacientes con diabetes
- primero limpieza y calidad del dato
- luego EDA
- después inferencia
- al final modelos interpretables

### Frase simple para decir

"Antes de modelar, primero entendimos la forma del dato. Eso nos ayudó a no usar pruebas o modelos que no correspondían."

## Diapositiva 3. Hallazgos exploratorios

### Mensaje principal

- la estancia tiene sesgo a la derecha
- la recurrencia tiene muchos ceros y mucha dispersión
- la readmisión cambia entre grupos de edad y tratamiento

### Visuales sugeridos

- tasa de readmisión por edad
- ECDF o gráfico principal de `time_in_hospital`

### Frase simple para decir

"El análisis exploratorio nos mostró que las variables importantes no se comportan de forma normal ni simple. Eso cambió nuestras decisiones estadísticas."

## Diapositiva 4. Evidencia estadística

### Mensaje principal

- normalidad débil para variables principales
- diferencias reales entre grupos
- asociación entre readmisión y algunas variables categóricas

### Ejemplos concretos

- Shapiro-Wilk rechazó normalidad en variables clave
- Mann-Whitney y K-S apoyaron diferencias entre pacientes readmitidos y no readmitidos
- chi-cuadrada mostró asociación entre readmisión y algunas variables de tratamiento o perfil del paciente

### Frase simple para decir

"Primero vimos patrones en gráficas. Después usamos pruebas para verificar que esos patrones no parecían casualidad."

## Diapositiva 5. Modelos y lectura simple

### Mensaje principal

- readmisión: GLM binomial
- recurrencia: Poisson vs binomial negativa
- estancia: GLM Gamma

### Qué decir del modelo de readmisión

"La señal más clara fue la historia previa de hospitalización. Quien ya tenía más admisiones previas también tendía a tener más riesgo de readmisión a 30 días."

### Qué decir del modelo de recurrencia

"Las visitas previas a urgencias y el uso previo del sistema fueron señales fuertes de recurrencia. Además, la binomial negativa confirmó que la recurrencia tiene más variación de la esperada en un Poisson simple."

### Qué decir del modelo de estancia

"Más diagnósticos, más admisiones previas y más medicamentos se relacionaron con estancias más largas. Eso apunta a complejidad clínica."

### Números útiles para mencionar

- readmisión: AUC aproximada `0.64`
- recurrencia: `alpha ≈ 1.56`
- estancia: RMSE aproximado `2.59`

## Diapositiva 6. Recomendaciones

### Mensaje principal

1. reforzar seguimiento al alta en pacientes con mayor uso previo del hospital
2. tratar la recurrencia como un problema concentrado en ciertos perfiles
3. usar señales de complejidad para anticipar estancias largas

### Frase simple para cerrar

"La idea central es sencilla: los pacientes más complejos y con más uso previo del hospital concentran buena parte del riesgo operativo."

## Preguntas que te pueden hacer

### ¿Por qué hiciste `readmitted` binaria?

"Porque el guideline pone el foco en readmisión dentro de 30 días. Así la variable queda alineada con la pregunta principal del hospital."

### ¿Por qué no borraste todos los faltantes?

"Porque había demasiados. Si borrábamos filas sin pensar, podíamos sesgar la muestra y perder información importante."

### ¿Por qué usaste pruebas no paramétricas?

"Porque varias variables no se veían normales y además tenían colas largas. Las pruebas robustas eran más coherentes con el dato."

### ¿Por qué binomial negativa para recurrencia?

"Porque la varianza era mayor que la media. Eso sugiere sobredispersión y hace más razonable una binomial negativa que un Poisson simple."

### ¿Por qué Gamma para estancia?

"Porque la estancia es positiva y sesgada a la derecha. Gamma respeta esa forma mejor que una regresión lineal simple."

### ¿Esto prueba causalidad?

"No. Prueba asociación estadística. Sirve para orientar decisiones, pero no para afirmar causa directa."
