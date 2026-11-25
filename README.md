# Agenda CeRa — Práctica 9 de PGPI

Simulación académica de la gestión de la configuración del software. Universidad de Granada, curso 2026/2027. 

La aplicación propuesta facilita la organización del tiempo y las actividades mediante una agenda accesible y personalizable. Los archivos `.txt` de este repositorio representan cambios de código, no son una aplicación ejecutable ni contienen datos reales del alumnado.

## Equipo

| Integrante | Función general (P1–P2) |
|---|---|
| Mercedes Lorenzo Aragón | Coordinación y dirección |
| Juan Carlos Montes Ronda | Planificación y gestión técnica |
| Manuel Martínez Cobos | Seguimiento y control de calidad |

## Tareas y ramas previstas

| Tarea | Referencia P3 | Rama | Responsable | Participantes |
|---|---|---|---|---|
| Agenda diaria/semanal | E03 / SCRUM-24 | `feature/agenda` | Juan Carlos | Juan Carlos y Mercedes |
| Gestión del comedor | E04 / SCRUM-11 | `feature/comedor` | Manuel | Manuel y Mercedes |

Las referencias SCRUM corresponden al backlog de P3 y Jira.

| Rama personal | Rama de origen | Integrante | Aportación |
|---|---|---|---|
| `feature/agenda-juancarlos` | `feature/agenda` | Juan Carlos | Modelo y filtrado de agenda |
| `feature/agenda-mercedes` | `feature/agenda` | Mercedes | Presentación accesible diaria/semanal |
| `feature/comedor-manuel` | `feature/comedor` | Manuel | Registro de comensales y dietas |
| `feature/comedor-mercedes` | `feature/comedor` | Mercedes | Generación del listado diario |

`main` es la rama estable. Los responsables inicializan dos archivos por tarea y cada participante desarrolla dos cambios en su rama personal. Las ramas personales se integran en la rama de tarea; después cada responsable integra su tarea en `main`. Se conservan las ramas para la evaluación y se utilizan merges sin squash.

## Versiones previstas

- `v1.0.0`: integración inicial de ambas tareas.
- `v1.0.1`: corrección de una incidencia registrada en Jira. Responsable: Mercedes. La rama `fix/CLAVE-NUMERO-listado-comedor` y su commit utilizarán la clave real de la incidencia. Los tags apuntarán a commits distintos de `main`.

## Archivos de simulación

- `agenda/modelo.txt`: datos, filtro temporal y orden de tareas.
- `agenda/vista.txt`: modo de visualización y presentación accesible.
- `comedor/registro.txt`: registro ficticio de comensales y dietas.
- `comedor/listado.txt`: generación simulada del informe de comedor.

## Control de calidad

Cada integración requiere revisar los cambios, comprobar que no se pierden aportaciones de otros miembros y conservar el historial. Se verifica la corrección del comedor comparando las dos versiones. Esta comprobación es documental, no una prueba de software en ejecución. No se incorporan datos reales ni material del centro.
