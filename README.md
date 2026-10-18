# Examen Unidad 2 — Fundamentos de Ciencia de Datos (TecNM)

**Actividad Integradora:** Inferencia Estadística y Toma de Decisiones en Ingeniería
**Caso seleccionado:** A — Arquitectura de Software (Monolito vs. Microservicios)
**Equipo:** Hernandez Barreto Alan Daleth, Alfonso Dominguez Gonzales

## Problema

¿La sobrecarga de red en microservicios incrementa la latencia de respuesta HTTP (ms) respecto a un monolito?

- Variable cuantitativa (Y): latencia de respuesta HTTP en ms
- Variable cualitativa (X): tipo de arquitectura (Monolito vs. Microservicios)
- Muestra: 250 observaciones por grupo (N = 500), generadas sintéticamente con distribuciones gamma (semilla 42)

## Estructura

```
.
├── data/
│   ├── dataset_caso_a.csv            # dataset original (500 registros)
│   └── dataset_caso_a_depurado.csv   # versión depurada 1.5×IQR (483 registros)
├── notebooks/
│   └── examen_fcd_u2.ipynb           # cuaderno ejecutable, documentado celda a celda
├── docs/
│   ├── reporte_tecnico.pdf           # reporte técnico (entregable)
│   ├── reporte_tecnico.tex           # fuente LaTeX
│   ├── referencias.bib
│   └── figures/                      # figuras generadas por el cuaderno
└── requirements.txt
```

## Cómo ejecutar

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute notebooks/examen_fcd_u2.ipynb
```

O en la nube (sin instalar nada):
- https://www.kaggle.com/code/dlthhb/examen-fcd-u2-monolito-vs-microservicios

## Resultados clave

| Prueba | Resultado |
|---|---|
| Levene (homogeneidad de varianzas) | W = 1.8419, p = 0.1754 → varianzas combinadas |
| IC 95% diferencia de medias (µ₁−µ₂) | [−9.63, 6.80] ms → **0 ∈ IC** |
| t de Student (bilateral, α = 0.05) | t = −0.3384, p = 0.7352 |
| Veredicto | **No se rechaza H₀** — sin evidencia de diferencia en latencia media |

Conclusión técnica: elegir entre monolito y microservicios por escalabilidad y despliegue, no por latencia media; al migrar, planificar tolerancia de hasta ~10 ms de sobrecarga potencial.
