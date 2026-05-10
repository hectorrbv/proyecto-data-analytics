# Proyecto Final — Analítica de Datos

**Universidad Iberoamericana · Primavera 2026**
**Materia:** Analítica de Datos
**Profesor:** Rodrigo Cárdenas Domínguez
**Alumnos:** Hector Raul Becerril Villamil · Elena Carolina Sánchez Araiza

Análisis de **readmisiones hospitalarias, recurrencia y duración de la estancia** en pacientes diabéticos, utilizando el dataset *Diabetes 130-Hospitals* (UCI).

---

## Estructura del repositorio

Este repositorio contiene las **tres iteraciones** del proyecto, en orden cronológico:

| Carpeta | Iteración | Descripción |
|---|---|---|
| [`proyecto/`](proyecto/) | **1ª — versión Codex** | Primera versión del análisis. Notebook en inglés, enfoque pedagógico con explicaciones extensas. Incluye reporte y dataset. |
| [`proyecto_claude/`](proyecto_claude/) | **2ª — versión Claude** | Segunda versión, en español, más compacta. Incluye reporte IEEE en LaTeX, presentación y figuras pulidas. |
| [`proyecto_unificado/`](proyecto_unificado/) | **3ª — versión final unificada** | **Entregable final.** Síntesis de las dos versiones anteriores, simplificada y validada. Notebook único en español sencillo, gráficas estilo notebook de clase, reporte final en PDF. |

---

## Entregable principal

Para revisar el proyecto final, ir directamente a:

- **Notebook:** [`proyecto_unificado/proyecto_final.ipynb`](proyecto_unificado/proyecto_final.ipynb)
- **Reporte:** [`proyecto_unificado/reporte_final/reporte_final.pdf`](proyecto_unificado/reporte_final/reporte_final.pdf)
- **Documentación:** [`proyecto_unificado/README.md`](proyecto_unificado/README.md)

---

## Resumen de los modelos

Tres preguntas, tres familias de distribución apropiadas:

| Pregunta | Modelo | Variable de respuesta |
|---|---|---|
| ¿Qué pacientes regresan en menos de 30 días? | Regresión **Logística** (Binomial / logit) | `readmit_30d` (binaria) |
| ¿Cuántas veces se interna un paciente? | **Poisson** vs **Binomial Negativa** | `number_inpatient` (conteo) |
| ¿Cuánto duran las estancias? | Regresión **Gamma** con liga log | `time_in_hospital` (continua positiva) |

---

## Requisitos

```
python >= 3.11
pandas, numpy, scipy
statsmodels, scikit-learn
matplotlib, seaborn
jupyter
```

Para correr el notebook final:

```bash
cd proyecto_unificado
jupyter notebook proyecto_final.ipynb
```

El dataset se carga automáticamente desde `proyecto_unificado/fuente_codex/diabetic_data.csv`.
