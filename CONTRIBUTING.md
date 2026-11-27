# Guía de contribución — Agenda CeRa

Agenda CeRa, proyecto académico de la asignatura Planificación y Gestión de Proyectos Informáticos (PGPI), Universidad de Granada, curso 2026/2027.

Esta guía establece las normas de trabajo colaborativo, control de versiones e integración de cambios para la práctica 9. Los archivos `.txt` simulan código: el repositorio no contiene una aplicación ejecutable. El alcance y las responsabilidades generales se describen en el [README](README.md).

La práctica ya está completada. Esta guía conserva las normas del proceso seguido y sirve como referencia: los comandos de creación de ramas y etiquetas son ejemplos históricos, no pasos pendientes que deban repetirse. Consulta el [CHANGELOG](CHANGELOG.md) para conocer las versiones publicadas.

## 1. Equipo y reparto de tareas

| Tarea | Responsable | Colaboradores | Rama de integración |
| --- | --- | --- | --- |
| Agenda diaria y semanal (E03 / SCRUM-24) | Juan Carlos Montes Ronda | Juan Carlos y Mercedes | `feature/agenda` |
| Gestión del comedor (E04 / SCRUM-11) | Manuel Martínez Cobos | Manuel y Mercedes | `feature/comedor` |

Mercedes Lorenzo Aragón coordina el repositorio, la publicación de las versiones y la gestión de la incidencia simulada en Jira. Cada responsable inicializa su tarea, revisa las aportaciones y realiza su integración final en `main`.

## 2. Preparación del entorno

Se necesita Git y acceso autorizado al repositorio de GitHub. Cada integrante debe utilizar su propia cuenta e identidad de Git.

```bash
git clone https://github.com/MercheLorenzo/agenda-cera-pgpi-p9.git
cd agenda-cera-pgpi-p9
git config user.name "Nombre y apellidos"
git config user.email "Correo verificado en GitHub"
git status
```

Utiliza tu correo verificado o la dirección `noreply` facilitada por GitHub. Si ya tienes el repositorio clonado, no vuelvas a clonarlo. Antes de comenzar una tarea, comprueba que no hay cambios locales pendientes y actualiza las referencias remotas con `git fetch origin`.

## 3. Estrategia de ramas

| Rama | Origen | Finalidad |
| --- | --- | --- |
| `main` | — | Rama estable; cambios revisados e integrados. |
| `feature/agenda` | `main` | Integración de la tarea de agenda. |
| `feature/agenda-juancarlos` | `feature/agenda` | Modelo, filtrado y orden de tareas. |
| `feature/agenda-mercedes` | `feature/agenda` | Vista diaria/semanal y accesibilidad. |
| `feature/comedor` | `main` | Integración de la tarea de comedor. |
| `feature/comedor-manuel` | `feature/comedor` | Registro de comensales, dietas y validación. |
| `feature/comedor-mercedes` | `feature/comedor` | Generación del listado diario. |
| `fix/CERA-1-listado-comedor` | `main` | Corrección definitiva asociada a CERA-1 e integrada en `main`. |
| `fix/CERAP-1-listado-comedor` | `main` | Rama histórica del espacio Jira empresarial; no integrar. |

Las dos ramas de tarea deben partir de `main` antes de integrar cualquiera de las dos tareas. Pueden existir cambios intermedios de documentación que no alteren el contenido funcional de partida. Cada responsable crea al menos dos archivos iniciales. Las ramas personales deben partir de la tarea ya inicializada, no directamente de `main`.

## 4. Flujo de contribución

1. Los responsables crean y publican las ramas `feature/agenda` y `feature/comedor` con sus archivos iniciales.
2. Cada participante crea su rama personal a partir de la rama de tarea correspondiente.
3. Cada participante realiza al menos dos commits con modificaciones reales en sus archivos de simulación y publica su rama.
4. Una vez terminados sus commits personales, cada miembro integra su aportación en la rama de tarea, de forma coordinada con el resto del equipo. Se coordina el orden de los merges para evitar cambios simultáneos sobre la misma rama.
5. Juan Carlos y Manuel revisan las dos aportaciones de sus respectivas tareas. Juan Carlos integra agenda en `main` y, después, Manuel integra comedor en `main`.
6. Mercedes publica `v1.0.0`, registra y corrige la incidencia de Jira y publica `v1.0.1` tras verificar la corrección.

### Ejemplo de creación de una rama personal

```bash
git fetch origin
git switch -c feature/agenda-juancarlos origin/feature/agenda
```

Después de editar el archivo correspondiente, revisar y registrar el cambio:

```bash
git status
git diff
git add agenda/modelo.txt
git commit -m "feat: definir campos y estados de agenda"
```

Repetir la edición y el commit para el segundo cambio. Publicar la rama al finalizar:

```bash
git push -u origin feature/agenda-juancarlos
```

Este ejemplo corresponde a Juan Carlos. Los demás integrantes deben utilizar su rama, su archivo y sus mensajes de commit correspondientes.

## 5. Convenciones de commits

Se utiliza una convención sencilla inspirada en Conventional Commits:

| Prefijo | Uso | Ejemplo |
| --- | --- | --- |
| `feat:` | Nueva funcionalidad simulada | `feat: incorporar filtros y orden de agenda` |
| `fix:` | Corrección de errores | `fix: excluir registros sin asistencia` |
| `docs:` | Documentación | `docs: añadir guia de contribucion` |
| `merge:` | Integración de ramas | `merge: integrar tarea agenda en main` |

Los mensajes deben ser breves, descriptivos y representar un cambio concreto. No se deben crear commits vacíos, atribuir aportaciones a otra persona ni agrupar los dos cambios personales en un único commit. Revisar `git diff` antes de preparar los archivos y `git diff --staged` antes de confirmar los cambios.

## 6. Integración y revisión de cambios

Se utilizarán merges sin squash para conservar el historial individual. Ejemplo de integración de una rama personal cuando todas las aportaciones estén publicadas:

```bash
git fetch origin
git switch feature/agenda
git pull --ff-only origin feature/agenda
git merge --no-ff origin/feature/agenda-juancarlos -m "merge: integrar juancarlos en agenda"
git push origin feature/agenda
```

Si la rama de tarea no existe localmente, crearla primero con `git switch --track origin/feature/agenda`. Si se utilizan pull requests, seleccionar **Create a merge commit** y no borrar la rama al finalizar. La rama de destino de una aportación personal es la rama de su tarea; la integración en `main` corresponde al responsable de la tarea.

Antes de integrar:

- [ ] La rama parte de la línea base adecuada.
- [ ] Se han realizado los dos commits personales exigidos.
- [ ] Los cambios se limitan a los archivos asignados y no eliminan aportaciones ajenas.
- [ ] Se han revisado el contenido, los criterios de accesibilidad y la coherencia de los datos ficticios.
- [ ] No quedan conflictos sin resolver ni archivos temporales o credenciales.

Si aparece un conflicto, revisar los archivos afectados con el compañero, resolverlo y comprobar el resultado antes de confirmar el merge. Si no se puede resolver todavía, `git merge --abort` permite abandonar un merge en curso. No utilizar `git push --force`, reescribir commits compartidos, borrar ramas de la práctica ni mover etiquetas publicadas.

## 7. Organización de archivos

| Archivo | Responsable de la aportación personal |
| --- | --- |
| `agenda/modelo.txt` | Juan Carlos |
| `agenda/vista.txt` | Mercedes |
| `comedor/registro.txt` | Manuel |
| `comedor/listado.txt` | Mercedes |

Guardar los archivos de texto en UTF-8. Mantener los nombres y la estructura del proyecto. El ZIP de preparación y su carpeta `archivos/` son material auxiliar local: no deben incorporarse al repositorio completo. No publicar datos reales del alumnado, credenciales, tokens, archivos privados del centro ni información personal innecesaria.

## 8. Gestión de incidencias con Jira

Tras publicar `v1.0.0`, se registra la incidencia simulada de comedor en Jira, con descripción, responsable y criterios de aceptación. La incidencia se vincula a GitHub usando su clave real tanto en la rama como en el commit.

Ejemplo histórico de la corrección definitiva (para futuras incidencias, sustituir `CERA-1` por la clave real asignada por Jira):

```bash
git switch main
git pull --ff-only origin main
git switch -c fix/CERA-1-listado-comedor
# Modificar y revisar comedor/listado.txt.
git add comedor/listado.txt
git commit -m "CERA-1 fix: excluir registros sin asistencia del listado"
git push -u origin fix/CERA-1-listado-comedor
```

Comprobar que Jira muestra la rama y el commit asociados. La responsable integra la corrección en `main` mediante un merge sin squash. La incidencia se cierra tras comprobar documentalmente el cambio y publicar la versión corregida. No registrar como ejecutadas pruebas que no se han realizado.

En la práctica, la incidencia inicial `CERAP-1` se trasladó desde un espacio empresarial a un espacio de desarrollo de software de Jira. La clave definitiva es [CERA-1](https://pgpi-practicas.atlassian.net/browse/CERA-1). La rama `fix/CERAP-1-listado-comedor` queda como histórico sin integrar; la rama `fix/CERA-1-listado-comedor` contiene la corrección definitiva. Se conserva la trazabilidad sin reescribir commits ni desplazar etiquetas.

## 9. Versionado y publicación

Se utilizan etiquetas anotadas de Git con el formato `vMAJOR.MINOR.PATCH`:

| Versión publicada | Contenido |
| --- | --- |
| `v1.0.0` | Agenda y comedor integrados en `main`. |
| `v1.0.1` | Corrección de CERA-1 integrada en `main`. |

Una vez comprobadas ambas tareas, la coordinadora crea la primera etiqueta:

```bash
git switch main
git pull --ff-only origin main
git tag -a v1.0.0 -m "Hito P9: agenda y comedor integrados"
git push origin v1.0.0
```

Después de integrar y verificar la corrección, crear la segunda etiqueta:

```bash
git switch main
git pull --ff-only origin main
git tag -a v1.0.1 -m "Hito P9: correccion de listado del comedor"
git push origin v1.0.1
```

Las etiquetas publicadas apuntan a `034f40d` (v1.0.0) y `69b73ba` (v1.0.1). No recrearlas ni desplazarlas. Los cambios posteriores exclusivamente documentales pueden incorporarse a `main` sin modificar las etiquetas. Las Releases de GitHub son opcionales.

## 10. Verificación y entrega

```bash
git fetch origin --tags
git branch -r
git log --graph --oneline --decorate --all
git tag -n
git diff v1.0.0 v1.0.1
git status
```

Comprobar que se conservan las contribuciones de los tres integrantes, las ramas de tarea y personales, las dos etiquetas y la asociación de la incidencia en Jira. La comparación de versiones es una verificación documental de los archivos de simulación, no una prueba de una aplicación en ejecución.

La entrega incluye el enlace al repositorio, los enlaces a las dos versiones y el enlace al proyecto de Jira. Garantizar el acceso del profesorado a los recursos según el enunciado. Se recomienda adjuntar el enlace directo a la incidencia como evidencia adicional. Los enlaces definitivos están recopilados en el [README](README.md), incluido el [espacio Jira](https://pgpi-practicas.atlassian.net/jira/software/projects/CERA/boards/34).

## 11. Comunicación y buenas prácticas

Mantener una comunicación respetuosa, avisar al equipo cuando se publica una rama o se completa una integración y consultar al responsable antes de cambiar el alcance de una tarea. Las contribuciones externas al equipo requieren autorización previa. Esta guía organiza el trabajo académico y no sustituye una licencia de software.

---

**Agenda CeRa · PGPI · Universidad de Granada · Curso 2026/2027**
