# Laboratorio académico clínico

Maqueta y plan inicial del **Laboratorio de Informática en Salud** de la Facultad de Medicina de la Universidad Nacional de Mar del Plata, en el marco de la **Unidad de Intervenciones Tecnológicas y Evidencias en Salud (UniTES)**.

El proyecto propone un entorno de enseñanza para trabajar con historias clínicas sintéticas, interoperabilidad, evaluación de tecnologías sanitarias y uso responsable de inteligencia artificial.

## Qué problema docente aborda

La formación médica incorpora cada vez más registros digitales, sistemas de información y herramientas de inteligencia artificial. Sin embargo, el estudiante necesita aprender a:

- leer una historia clínica longitudinal y no solo un dato aislado;
- distinguir datos, observaciones, problemas e interpretaciones;
- reconocer qué evidencia sostiene una afirmación clínica;
- identificar datos faltantes o contradictorios;
- comprender los límites de una herramienta digital antes de utilizarla en salud.

La maqueta no contiene datos de pacientes reales y no está destinada a la atención clínica.

## Caso de uso resuelto

### Caso sintético SH-1047

Lucía M. tiene 42 años. En la historia aparecen antecedentes de hipertensión arterial y asma. La línea temporal contiene tres encuentros:

1. Consulta inicial de clínica médica, 18 de abril de 2023.
2. Control y laboratorio, 7 de agosto de 2024.
3. Consulta por disnea de esfuerzo, 12 de marzo de 2025.

### Consigna para el estudiante

> Reconstruir el problema clínico actual, relacionarlo con los antecedentes y señalar qué información adicional debería revisarse antes de formular una interpretación.

### Resolución sintética esperada

**Problema actual:** disnea de esfuerzo referida en el último encuentro.

**Antecedentes relevantes:** asma e hipertensión arterial, que deben interpretarse junto con la evolución temporal y los registros disponibles.

**Evidencia recuperada:** fecha y motivo del último encuentro, antecedentes documentados, resultados de laboratorio disponibles y relación con los encuentros previos.

**Información faltante que debe identificarse:** signos vitales, saturación de oxígeno, examen físico, medicación actual y adherencia, características temporales del síntoma y estudios complementarios si la pregunta clínica los requiere.

**Conclusión docente:** con los datos sintéticos disponibles no corresponde cerrar un diagnóstico. La respuesta adecuada es delimitar el problema, citar la evidencia y explicitar qué información falta.

El objetivo no es que la herramienta “adivine” un diagnóstico. El objetivo es que el estudiante pueda justificar qué sabe, qué no sabe y qué debería revisar.

## Flujo de trabajo de la maqueta

1. El estudiante abre un caso sintético.
2. Revisa la línea temporal y los recursos estructurados del paciente.
3. Selecciona una actividad: reconstrucción del caso, jerarquización de hallazgos, resumen clínico o discusión de evidencia.
4. Consulta una síntesis asistida que mantiene referencias a los encuentros de origen.
5. Redacta su propia respuesta y señala los datos faltantes.
6. El docente revisa la respuesta con una rúbrica y analiza el razonamiento en clase.

## Qué haría el laboratorio

UniTES no sería solamente una aplicación web. Sus funciones académicas previstas son:

- formar en competencias digitales y salud digital;
- enseñar calidad del dato, historia clínica electrónica e interoperabilidad;
- producir y discutir informes rápidos de evidencia para problemas sanitarios;
- investigar implementación de sistemas de información y tecnologías;
- evaluar tecnologías sanitarias con criterios éticos, regulatorios y contextuales;
- desarrollar materiales docentes y casos sintéticos reutilizables.

## Rol de la inteligencia artificial

La IA se utilizaría como apoyo para el aprendizaje y la investigación, no como autoridad clínica ni como reemplazo del docente.

### Funciones permitidas en el prototipo

- extraer entidades y eventos de notas clínicas sintéticas;
- ordenar información en una línea temporal;
- recuperar evidencia vinculada con una afirmación;
- generar un borrador de resumen clínico con referencias a encuentros;
- señalar datos ausentes, inconsistencias o necesidad de revisión;
- ofrecer retroalimentación preliminar según una rúbrica docente.

### Funciones que no debe realizar

- emitir diagnósticos o tratamientos autónomos;
- ocultar la fuente de una afirmación;
- completar datos no registrados como si fueran verdaderos;
- evaluar estudiantes sin una rúbrica revisada por docentes;
- procesar datos identificables en servicios externos sin autorización institucional.

### Otras tareas posibles de la IA sobre la HCE

Además de ordenar la información, recuperar evidencia y generar borradores, el prototipo puede estudiar:

- captura y estructuración de texto, voz y formularios;
- extracción de problemas, antecedentes, medicación, resultados y planes;
- detección de faltantes, duplicaciones, inconsistencias y contradicciones;
- sugerencia de codificación y mapeo entre SNOMED CT, LOINC, CIE-10 y perfiles locales;
- sistemas de soporte a la toma de decisión basados en reglas o guías, con fuentes visibles;
- alertas de resultados pendientes, controles vencidos, interacciones o tendencias;
- identificación de cohortes para docencia, auditoría, investigación y planificación;
- auditoría de calidad, completitud y consistencia del registro;
- retroalimentación de actividades docentes mediante rúbricas revisadas por docentes;
- preparación de síntesis de evidencia e informes para la gestión sanitaria.

El grado de automatización debe ser diferente según el riesgo. Estructurar o recuperar información no equivale a recomendar una conducta clínica. Las funciones de soporte a la decisión deben mostrar reglas, evidencia, incertidumbre y límites, y nunca reemplazar el juicio profesional.

## Qué IA se propone evaluar

La maqueta publicada todavía **no tiene una IA conectada**. La propuesta para un piloto es evaluar un modelo de lenguaje de código abierto, ejecutado dentro de la infraestructura de la Facultad, con recuperación de contexto y supervisión humana.

Como candidatos iniciales pueden evaluarse **Qwen2.5 7B Instruct** y **Llama 3.1 8B Instruct**. La elección no debe hacerse por popularidad: se debe comparar su desempeño en español, estabilidad, capacidad de citar fuentes, costo computacional y comportamiento ante datos faltantes. Ninguno se considerará validado para decisiones clínicas por el solo hecho de funcionar en la maqueta.

La arquitectura propuesta es:

```text
Historia sintética / FHIR
          ↓
Normalización y terminologías
          ↓
Recuperación de encuentros y evidencia
          ↓
Modelo de lenguaje local
          ↓
Respuesta con fuentes + datos faltantes + advertencias
          ↓
Revisión del estudiante y del docente
```

El modelo debe recibir únicamente el contexto seleccionado, devolver referencias a los recursos de origen y dejar trazabilidad de la versión del modelo y del prompt utilizado.

## Componentes técnicos previstos

- **Interfaz:** página web docente para casos, actividades y discusión.
- **Datos:** pacientes y encuentros sintéticos.
- **Interoperabilidad:** HL7 FHIR R4, con perfiles docentes locales.
- **Terminologías:** SNOMED CT, LOINC y otros conjuntos definidos por la Facultad.
- **Recuperación:** consultas FHIR y, si se necesita búsqueda semántica, un índice vectorial institucional.
- **IA:** servicio local de inferencia, separado de la interfaz y registrando modelo, versión y fuentes.
- **Evaluación:** rúbrica docente, conjuntos de casos y revisión de errores.

## Estado actual

- La página académica está publicada como maqueta estática.
- El caso SH-1047 está representado con datos sintéticos.
- Las interacciones actuales son demostrativas.
- El endpoint FHIR es una referencia visual, no un servidor operativo.
- La IA, el almacenamiento persistente, la autenticación y la evaluación automática todavía no están implementados.

## Próximos pasos

1. Validar el caso de uso y la rúbrica con docentes de la Facultad.
2. Crear un pequeño conjunto de casos sintéticos en español.
3. Implementar un servidor FHIR de prueba.
4. Comparar los modelos candidatos con tareas acotadas y criterios explícitos.
5. Incorporar un servicio local de recuperación y generación con trazabilidad.
6. Probar el entorno con estudiantes y revisar los errores antes de ampliar el alcance.

## Enlaces

- [Arquitectura inicial](ARQUITECTURA.md)
- [Despliegue institucional](DESPLIEGUE-FACULTAD.md)
- [Maqueta publicada](https://manwithbarba.github.io/laboratorio-academico-clinico/)
