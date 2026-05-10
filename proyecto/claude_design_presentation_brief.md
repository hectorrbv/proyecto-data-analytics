# Instrucciones para Claude Design

Necesito que me ayudes a crear una presentación de **5 a 6 diapositivas** para un proyecto final de Data Analytics sobre pacientes con diabetes.

## Objetivo de la presentación

Explicar de forma clara y sencilla:

1. qué problema quería resolver el hospital
2. qué se encontró en los datos
3. qué pruebas estadísticas se usaron
4. qué modelos se eligieron y por qué
5. qué recomendaciones se pueden dar

La presentación no debe verse técnica en exceso ni saturada de texto. Debe verse como una presentación corta, clara y profesional para clase.

## Audiencia

- profesor
- compañeros de clase
- nivel académico universitario

## Tono

- profesional
- claro
- visual
- simple
- sin lenguaje rebuscado

## Estilo visual

- limpio
- moderno
- fondo claro
- acentos en verde oscuro, azul petróleo o gris
- evitar morado como color principal
- evitar apariencia demasiado corporativa o demasiado “tech”
- usar buena jerarquía visual
- poco texto por diapositiva
- una idea fuerte por slide

## Regla importante

Cada diapositiva debe responder una pregunta simple. No quiero párrafos largos. Quiero frases cortas, datos clave y una visual fuerte.

## Estructura de diapositivas

### Diapositiva 1. Problema y objetivo

Idea principal:

El hospital quiere entender tres cosas:

1. quién tiene más riesgo de readmisión en menos de 30 días
2. quién tiende a regresar varias veces
3. quién tiende a quedarse más tiempo

Texto sugerido:

**Problema**
Las readmisiones, la recurrencia hospitalaria y las estancias largas afectan al paciente y también a la operación del hospital.

**Objetivo**
Encontrar patrones que ayuden a entender mejor estos tres fenómenos en pacientes con diabetes.

Visual sugerida:

- una portada con concepto de hospital, datos y pacientes
- puede ser un fondo visual suave con espacio limpio para texto

### Diapositiva 2. Datos y método

Idea principal:

Primero se entendió el dato y luego se modeló.

Texto sugerido:

**Datos**
- 101,766 registros
- pacientes con diabetes
- hospitales de Estados Unidos

**Proceso**
- limpieza del dato
- EDA
- inferencia estadística
- modelos interpretables

Visual sugerida:

- diagrama simple de flujo
- o timeline corto de 4 pasos

### Diapositiva 3. Hallazgos exploratorios

Idea principal:

Las variables principales no tienen una forma simple.

Texto sugerido:

**Hallazgos**
- la estancia tiene sesgo a la derecha
- la recurrencia tiene muchos ceros y mucha dispersión
- la readmisión cambia entre grupos de edad y tratamiento

Visual sugerida:

- una gráfica de tasa de readmisión por edad
- y una visual secundaria pequeña de distribución o ECDF

### Diapositiva 4. Evidencia estadística

Idea principal:

Los patrones visuales también se sostienen con pruebas estadísticas.

Texto sugerido:

**Pruebas usadas**
- Shapiro-Wilk
- Levene
- Mann-Whitney
- Kolmogorov-Smirnov
- Chi-cuadrada

**Conclusión**
- las variables principales no se comportan como normales limpias
- sí hay diferencias reales entre grupos

Visual sugerida:

- tabla pequeña con 3 pruebas clave
- o bloques tipo “prueba / qué mostró”

### Diapositiva 5. Modelos y lectura simple

Idea principal:

Cada variable necesitó un modelo distinto.

Texto sugerido:

**Readmisión**
- GLM binomial
- AUC aproximada: 0.64

**Recurrencia**
- Poisson vs Binomial Negativa
- alpha aproximada: 1.56

**Estancia**
- GLM Gamma
- RMSE aproximado: 2.59

Lectura simple:

- más admisiones previas aumentan el riesgo de readmisión
- más uso previo de urgencias se relaciona con más recurrencia
- más diagnósticos y más medicamentos se relacionan con estancias más largas

Visual sugerida:

- tres tarjetas o columnas, una por modelo

### Diapositiva 6. Recomendaciones

Idea principal:

El hospital debe concentrarse en pacientes más complejos y con más uso previo del sistema.

Texto sugerido:

**Recomendaciones**
1. reforzar el seguimiento al alta
2. detectar perfiles con mayor recurrencia
3. usar señales de complejidad para anticipar estancias largas

Frase final:

Los pacientes más complejos y con más uso previo del hospital concentran buena parte del riesgo operativo.

Visual sugerida:

- cierre con 3 recomendaciones visuales
- diseño limpio y fuerte

## Qué no quiero

- demasiado texto
- lenguaje demasiado técnico
- diapositivas saturadas
- tablas grandes
- fondo oscuro pesado
- decoraciones que distraigan

## Qué sí quiero

- claridad
- buena jerarquía visual
- lenguaje simple
- números clave visibles
- una historia que fluya bien de slide a slide

## Si puedes mejorar algo, hazlo

Si ves una manera de hacerla más clara visualmente, hazlo, pero sin cambiar la idea principal del proyecto.
