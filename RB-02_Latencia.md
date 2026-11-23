# RB-02 | Latencia y continuidad del servicio

**Objetivo:** recuperar la velocidad de evaluación ante un deterioro sostenido.

**Activación:** alerta P1 por consumo acelerado del presupuesto de latencia en ventanas de 100 y 300 solicitudes.

1. Identificar la etapa que concentra la demora mediante métricas y trazas.
2. Desactivar el componente o configuración que causa la lentitud; conservar el modelo validado.
3. Repetir solicitudes de prueba y evaluar el indicador de respuestas dentro de 40 ms.
4. Mantener la vigilancia hasta que la alerta registre recuperación y no reaparezcan fallas.
5. Documentar el evento y el tiempo de restablecimiento.

**Responsables:** operación analítica y coordinación del servicio.

**Alcance de prueba:** se elimina automáticamente una demora agregada artificialmente al ciclo de inferencia.
