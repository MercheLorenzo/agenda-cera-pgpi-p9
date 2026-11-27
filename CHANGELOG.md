# Registro de cambios — Agenda CeRa

Este documento recoge los hitos publicados de la simulación académica de gestión de la configuración del software (PGPI, UGR, 2026/2027). Los números de versión identifican estados de los archivos de simulación, no entregas de una aplicación ejecutable.

## [Sin publicar]

### Documentación

- Actualización del README y la guía de contribución para reflejar el estado final, las versiones publicadas y la incidencia CERA-1.
- Incorporación de este registro de cambios.

Estos cambios documentales son posteriores a `v1.0.1` y no forman parte de esa etiqueta.

## [v1.0.1] — 2026-11-27

### Corregido

- Incidencia [CERA-1](https://pgpi-practicas.atlassian.net/browse/CERA-1): el listado del comedor incluía registros con asistencia negativa.
- En `comedor/listado.txt`, se modifica la regla de inclusión para seleccionar únicamente los registros de la fecha solicitada con `asistencia=si`.
- El ejemplo del 25/11/2026 pasa de tres comensales (E01, E02 y E03) a dos (E01 y E03). E02 queda excluido por asistencia negativa; E04, por fecha distinta.
- Se mantienen las reglas de agrupación por aula y dieta y las restricciones de acceso descritas en el archivo.

### Trazabilidad

- Responsable: Mercedes Lorenzo Aragón.
- Rama definitiva: `fix/CERA-1-listado-comedor`.
- Commit de corrección: [`4960f21`](https://github.com/MercheLorenzo/agenda-cera-pgpi-p9/commit/4960f216a3ef87421ea1fb35cc2868cab5c5e334).
- Merge y destino de la etiqueta: [`69b73ba`](https://github.com/MercheLorenzo/agenda-cera-pgpi-p9/commit/69b73ba15810e6d0f9c0aa4bd4f3ee923591aaff).
- Incidencia vinculada mediante GitHub for Atlassian y cerrada en Jira.
- La rama anterior `fix/CERAP-1-listado-comedor` se conserva sin integrar como histórico del traslado de la incidencia desde el espacio empresarial al espacio de software.

### Verificación

La comparación `git diff v1.0.0 v1.0.1` muestra un único archivo modificado (`comedor/listado.txt`), con tres inserciones y tres eliminaciones. La validación es documental, con datos ficticios.

## [v1.0.0] — 2026-11-26

### Añadido

- Agenda diaria y semanal: modelo de tareas, filtros, orden y preferencias de accesibilidad (`agenda/modelo.txt`, `agenda/vista.txt`).
- Gestión del comedor: registro de comensales, dietas y listado diario (`comedor/registro.txt`, `comedor/listado.txt`).
- README y guía de contribución con el reparto de responsabilidades y la estrategia de ramas.

### Integración

- Dos tareas, cuatro ramas personales y ocho commits personales de desarrollo.
- Cuatro merges de aportaciones personales y dos merges de tareas en `main`.
- Destino de la etiqueta: [`034f40d`](https://github.com/MercheLorenzo/agenda-cera-pgpi-p9/commit/034f40dd10264d4ba510eb40fd90394760bdca98).

### Defecto conocido

El listado de comedor no filtra por asistencia; incluye todos los registros de la fecha. Este defecto simulado se resuelve en `v1.0.1`.

[v1.0.1]: https://github.com/MercheLorenzo/agenda-cera-pgpi-p9/compare/v1.0.0...v1.0.1
[v1.0.0]: https://github.com/MercheLorenzo/agenda-cera-pgpi-p9/tree/v1.0.0
