# Despliegue institucional

## Primera etapa

1. Publicar la maqueta en GitHub Pages.
2. Validar contenidos y actividades con docentes de la Facultad de Medicina.
3. Definir el conjunto de datos sintéticos y la rúbrica de evaluación.
4. Implementar una API FHIR R4 en un servidor institucional de prueba.

## Servidor de la Facultad

- Sistema operativo Linux institucional actualizado.
- Proxy reverso con HTTPS.
- Aplicación web separada de la API.
- PostgreSQL para los datos de práctica.
- Copias de seguridad y auditoría.
- Sin datos identificables en el entorno docente.

## Acceso

La autenticación deberá integrarse con la identidad institucional. Los roles mínimos son estudiante, docente y administrador técnico.
