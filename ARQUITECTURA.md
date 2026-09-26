# Arquitectura del Laboratorio académico clínico

## Propósito

Maqueta académica para trabajar con historias clínicas sintéticas, razonamiento clínico longitudinal y contenidos de UniTES.

## Capas previstas

- Interfaz docente: casos sintéticos, actividades y evidencia clínica.
- API institucional: recursos HL7 FHIR R4.
- Datos: pacientes sintéticos, encuentros, observaciones, problemas y planes.
- Evaluación docente: consignas, rúbricas y registro de entregas.
- Seguridad: control de acceso, auditoría y separación estricta de datos reales.

## Principio de implementación

La página pública es una maqueta estática. El servidor de la Facultad deberá alojar la API y la base de datos en infraestructura institucional, con datos sintéticos durante la etapa de enseñanza y validación.
