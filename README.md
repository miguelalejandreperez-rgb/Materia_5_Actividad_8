# Monitorización inteligente del riesgo crediticio

**Actividad 8 · Gestión de Proyectos de Inteligencia Artificial**  
**Miguel Ángel Alejandre Pérez · 22 de noviembre de 2026**

## Propuesta de valor

Un modelo de riesgo crediticio no solo debe identificar posibles incumplimientos: también debe mantener la calidad de sus predicciones, responder oportunamente y permitir una reacción ordenada ante fallas. Esta propuesta incorpora **monitorización preventiva, alertas inteligentes y protocolos de recuperación** a un modelo previamente desarrollado.

El objetivo es dar mayor confianza a la operación mediante tres capacidades: **anticipar desviaciones**, **priorizar incidentes** y **demostrar la recuperación** con indicadores claros. Las predicciones son señales de apoyo para el análisis; no reemplazan el juicio de quien toma decisiones crediticias.

## Resultados principales

| Indicador | Resultado |
|---|---:|
| Registros históricos de prueba | 6,000 |
| ROC-AUC del modelo | 0.7775 |
| Recall de incumplimiento | **81.54%** |
| Precision del modelo | 33.13% |
| Umbral de alerta crediticia | 0.14 |
| Inferencias de referencia correctas | **500 de 500** |
| Respuestas dentro de 40 ms | **99.6%** |
| Pruebas de alertas satisfactorias | **9 de 9** |
| Incidentes simulados y recuperados | **2** |

Estos resultados muestran que el sistema permite observar tanto la calidad predictiva como la continuidad del proceso de evaluación. El recall elevado favorece la identificación de posibles incumplimientos; la precision exige revisar las alertas con criterio de negocio para evitar decisiones precipitadas.

## Respuesta ante incidentes

| Situación simulada | Indicador de referencia | Durante el incidente | Después de la respuesta |
|---|---:|---:|---:|
| Alteración de información de pagos | Recall: 81.54% | Recall: 70.31% | Recall: **81.54%** |
| Aumento de latencia | p95: 39.02 ms | p95: 86.87 ms | p95: **5.26 ms** |

**Incidente 1 — Calidad de datos.** Se detectó un deterioro en la capacidad de identificar incumplimientos después de alterar de forma controlada información de pagos. El procedimiento `RB-03` permitió restituir los datos validados y recuperar la referencia de desempeño.

**Incidente 2 — Latencia.** Se introdujo una demora controlada que rebasó el objetivo de respuesta. El sistema emitió una alerta crítica y aplicó el procedimiento `RB-02` para retirar la causa, comprobar la mejora y registrar el cierre.

![Indicadores antes, durante y después de las intervenciones](04_Evidencia_Original/figuras/01_antes_durante_despues.png)

## Monitorización y alertas

La solución integra métricas, registros de eventos, trazas y seguimiento de ejecuciones con MLflow. Un tablero reúne indicadores de calidad y servicio; las reglas de alertamiento emplean ventanas de evaluación, prioridades y control de avisos repetidos.

| Objetivo de servicio (SLO) | Meta |
|---|---:|
| Inferencias procesadas correctamente | **99% o más** |
| Respuestas completadas en 40 ms o menos | **95% o más** |

Los presupuestos de error permiten distinguir una variación aislada de una afectación que merece intervención. Los indicadores de cambios en datos (*data drift*) complementan la vigilancia de calidad, sin sustituir la verificación del modelo con resultados observados.

![Dashboard de seguimiento](04_Evidencia_Original/figuras/02_dashboard_slo.png)

## Cómo ejecutar el proyecto

**Solo se necesita un notebook de Google Colab.** El modelo validado y sus referencias están integrados; no es necesario cargar archivos ZIP de actividades anteriores, configurar Docker ni desplegar una API.

1. Abrir [Actividad_8_Incidentes_Recuperacion.ipynb](02_Codigo/Actividad_8_Incidentes_Recuperacion.ipynb) en [Google Colab](https://colab.research.google.com/).
2. Seleccionar **Entorno de ejecución → Ejecutar todas**. Se requiere conexión a internet para instalar dependencias y obtener el conjunto de datos público.
3. Revisar las tablas y gráficas de resultados, los registros de MLflow, las alertas y las intervenciones de cada incidente.
4. Descargar el paquete `actividad8_resultados_integrales.zip` generado por el notebook al finalizar.

La ejecución utiliza el entorno de Colab y registra MLflow en SQLite dentro de la misma sesión. El archivo `02_Codigo/requirements.txt` documenta las dependencias y sus versiones.

## Contenido del repositorio

```text
.
├── README.md
├── 01_Documentos/
│   ├── 01_Documento_Tecnico.pdf        (+ .docx)
│   ├── 02_Evidencias_Implementacion.pdf (+ .docx)
│   └── 03_Simulacion_Incidentes.pdf    (+ .docx)
├── 02_Codigo/
│   ├── Actividad_8_Incidentes_Recuperacion.ipynb
│   └── requirements.txt
├── 03_Configuracion_y_Runbooks/
│   ├── configuracion_alertas.json
│   ├── RB-02_Latencia.md
│   └── RB-03_Calidad_Datos.md
└── 04_Evidencia_Original/
    ├── figuras/
    ├── incidentes/
    ├── logs/
    ├── mlflow_actividad8.db
    └── actividad8_resultados_integrales.zip
```

Los documentos presentan el diseño de la propuesta, los resultados visuales y la respuesta a los incidentes. Los registros originales respaldan la trazabilidad de las mediciones.

## Recomendación de negocio

La propuesta puede servir como base para un **piloto interno supervisado**, enfocado primero en la estabilidad de las señales de riesgo y la oportunidad de respuesta ante desviaciones. El siguiente paso para una adopción real sería validar indicadores con datos recientes y establecer responsables y acuerdos de atención acordes con la operación de la organización.

Los incidentes aquí descritos son **simulaciones controladas con datos históricos**. La disponibilidad y los tiempos registrados corresponden al entorno de prueba, no a la operación de un servicio en producción.
