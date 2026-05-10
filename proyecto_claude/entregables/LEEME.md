# Entregables — Proyecto Final de Analítica de Datos

**Hector Raul Becerril Villamil · Elena Carolina Sánchez Araiza**
Universidad Iberoamericana · Primavera 2026

## Archivos incluidos

| Archivo | Qué es |
| --- | --- |
| `proyecto_final_readmisiones.ipynb` | Jupyter Notebook completo, ya ejecutado (con outputs y figuras inline). |
| `reporte_ieee.tex` | Reporte profesional en formato IEEE, listo para compilar a PDF. |
| `esquema_presentacion.docx` | Esquema de las 6 diapositivas con bullets, imágenes sugeridas y guión por diapositiva. |
| `figuras/` | PNG de alta resolución que usan tanto el reporte como la presentación. |

## Cómo compilar el reporte LaTeX

Si no tienes LaTeX instalado localmente, lo más fácil es subir `reporte_ieee.tex` y la carpeta `figuras/` a [Overleaf](https://www.overleaf.com/) (proyecto nuevo → IEEE Conference Template → reemplazar el `.tex`).

Con instalación local (MacTeX / TeX Live):
```bash
pdflatex reporte_ieee.tex
pdflatex reporte_ieee.tex   # segunda pasada para referencias cruzadas
```

## Para re-ejecutar el notebook

Requiere: `python 3.9+`, `pandas`, `numpy`, `scipy`, `statsmodels`, `scikit-learn`, `matplotlib`, `seaborn`.

```bash
pip install pandas numpy scipy statsmodels scikit-learn matplotlib seaborn
jupyter notebook proyecto_final_readmisiones.ipynb
```

La ruta al dataset está hardcodeada como `/Users/hectorbecerrilvillamil/Desktop/ibero/DataAnalytics/proyecto/diabetic_data.csv` — si cambias de máquina, ajusta la constante `RUTA_DATOS` en la primera celda.

## Resumen de resultados numéricos

- **Dataset final:** 69,970 pacientes únicos tras limpieza.
- **Readmisión <30 d:** tasa base 8.97%; modelo logístico AUC = 0.608.
- **Recurrencia:** Binomial Negativa gana a Poisson con ΔAIC ≈ 8,500.
- **Estancia:** Gamma GLM (log-link), pseudo R² = 0.284.
