# Proyecto Unificado — Readmisiones, Recurrencia y Estancia Hospitalaria

**Universidad Iberoamericana · Primavera 2026**
Hector Raul Becerril Villamil · Elena Carolina Sánchez Araiza

---

## Entrada principal

**`proyecto_final.ipynb`** — notebook unificado, simplificado y comentado en español.

Es el único archivo que necesitas abrir. Contiene:

1. Carga y auditoría de datos
2. Limpieza con justificación de cada decisión (incluida la razón por la que **no** se usa MICE)
3. EDA con gráficas estilo notebook de clase (4 paneles diagnósticos: histograma + ECDF + boxplot + QQ)
4. Inferencia (KS, Mann-Whitney, Chi², Kruskal-Wallis)
5. **Modelo logístico** para readmisión a 30 días + ROC + forest plot de OR
6. **Poisson vs Binomial Negativa** para recurrencia + comparación AIC
7. **Regresión Gamma** para estancia + diagnóstico de residuos
8. Conclusiones y recomendaciones

### Cómo correrlo

```bash
cd proyecto_unificado
jupyter notebook proyecto_final.ipynb
```

El notebook lee el CSV desde `fuente_codex/diabetic_data.csv` (ruta relativa).

---

## Estructura de la carpeta

```
proyecto_unificado/
├── proyecto_final.ipynb       ← ENTRADA PRINCIPAL
├── README.md
├── reporte_final/             ← reporte LaTeX/PDF + figuras seleccionadas
├── fuente_codex/              ← notebook original (versión Codex), incluye el CSV
├── fuente_claude/             ← notebook original (versión Claude) + reporte IEEE
├── graficas/                  ← galería de PNG exportados (todas + importantes)
└── comparacion/               ← análisis Codex vs Claude vs trabajos previos
```

### ¿Qué pasó con las versiones anteriores?

Se conservan intactas:

- `fuente_codex/final_readmissions_project.ipynb` — versión pedagógica en inglés (62 celdas).
- `fuente_claude/entregables/proyecto_final_readmisiones.ipynb` — versión técnica en español (35 celdas).

`proyecto_final.ipynb` es una **síntesis** de ambas:

- Idioma de Codex (español sencillo, primera persona) + estructura de Claude (compacta).
- Gráficas del estilo del notebook de clase (`distributions/`, `inference/`, `MICE/`).
- Comentarios en línea que explican el *qué* y el *porqué* de cada paso.
- Se eliminó código duplicado y se consolidó la lógica en funciones cortas.

---

## Reporte final

- `reporte_final/reporte_final.pdf` — PDF listo para entregar.
- `reporte_final/reporte_final.tex` — fuente LaTeX (compilable con `pdflatex`).
- `reporte_final/figuras/` — PNG de las 5 figuras del reporte.

---

## Galería de gráficas

- `graficas/todas/` — todas las figuras exportadas del análisis exploratorio.
- `graficas/importantes/` — subconjunto seleccionado para reporte y presentación.
- `graficas/contact_sheet_*.png` — hojas visuales (índice rápido).
