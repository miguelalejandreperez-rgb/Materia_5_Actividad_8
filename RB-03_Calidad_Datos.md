# RB-03 | Calidad de predicciones y datos

**Objetivo:** evitar decisiones basadas en información de comportamiento de pago alterada.

**Activación:** alerta de drift (PSI >= 0.10) o recall inferior al 78% con al menos 1,000 etiquetas y 200 incumplimientos reales.

1. Confirmar que la variación exceda el nivel habitual y revisar el origen de los datos.
2. Suspender la transformación defectuosa y recuperar la última versión de datos verificada.
3. Ejecutar la evaluación del modelo conservando su versión e idéntico umbral crediticio.
4. Comparar recall, precision y distribución de predicciones antes, durante y después.
5. Registrar la intervención y solicitar aprobación de negocio antes de reanudar cualquier uso operativo.

**Responsables:** analítica de riesgos y responsable del modelo.

**Alcance de prueba:** se revierte una alteración introducida deliberadamente sobre una copia del dataset histórico.
