# Comparacion Codex vs Claude

## Resumen rapido

Las dos versiones resuelven el proyecto, pero con estilos distintos.

La version Claude esta mas cerca de un entregable profesional ya armado: trae reporte IEEE, figuras exportadas, notebook compacto y una historia mas ejecutiva.

La version Codex es mas didactica: explica mejor el proceso, sigue mas de cerca el estilo de los notebooks del curso y usa lenguaje mas sencillo para presentacion.

## Diferencias principales

| Aspecto | Version Codex | Version Claude | Mejor uso |
| --- | --- | --- | --- |
| Enfoque | pedagogico y explicado paso a paso | profesional y compacto | combinar ambos |
| Limpieza | conserva mas registros, menos agresiva | reduce a pacientes unicos y excluye terminales | Claude para muestra final |
| Tamano analitico | 101,766 encuentros | 69,970 pacientes | depende de la pregunta |
| Reporte | simple, claro, en formato article | IEEE mas acabado y tecnico | reporte unificado simple |
| Figuras | pocas, embebidas en notebook | 7 figuras PNG listas | Claude para reporte |
| Modelos | GLM binomial, Poisson/NB, Gamma | logistica, Poisson/NB, Gamma | ambos coinciden |
| Lenguaje | muy facil de explicar | mas tecnico y formal | Codex para exposicion |

## Diferencias numericas

| Resultado | Codex | Claude |
| --- | ---: | ---: |
| AUC readmision | 0.64 aprox. | 0.608 |
| Efecto admisiones previas | OR aprox. 1.31 | OR aprox. 1.40 |
| Sobredispersion recurrencia | alpha aprox. 1.56 | Delta AIC aprox. 8,500 |
| Estancia | RMSE aprox. 2.59 | pseudo R2 aprox. 0.284 |

Estas diferencias no son contradicciones graves. Salen de decisiones distintas de limpieza y de unidad de analisis:

- Codex trabaja mas cerca del dataset completo de encuentros.
- Claude trabaja con una muestra mas limpia de pacientes unicos.

## Que conviene conservar de Claude

- Figuras finales en PNG.
- Limpieza mas estricta para independencia de observaciones.
- Agrupacion diagnostica.
- Reporte con citas y estructura profesional.
- Seccion fuerte de recomendaciones.

## Que conviene conservar de Codex

- Lenguaje mas sencillo.
- Explicacion clara de por que cada modelo corresponde a cada variable.
- Enfoque alineado al curso: EDA, inferencia y modelos interpretables.
- Guion de presentacion.

## Decision para la version unificada

La carpeta `reporte_final/` usa una mezcla:

- graficas de Claude porque estan mejor preparadas para reporte;
- lenguaje de Codex porque es mas claro para presentar;
- estructura propia, mas corta, para no saturar el entregable.

## Figuras seleccionadas para el reporte

Se eligieron cinco:

1. `fig1_distribuciones.png`
2. `fig2_readmit_edad.png`
3. `fig3_corr_spearman.png`
4. `fig4_or_logistica.png`
5. `fig5_diag_gamma.png`

No se metieron todas al reporte porque eso lo vuelve pesado. Todas las graficas quedan disponibles en `graficas/todas/` para revisarlas en VS Code.

