# team-workflow

[English](README.md) · Español

Acompaña el trabajo de un equipo de software desde los requisitos hasta la integración, conectando tareas, tarjetas de Trello, issues de GitHub, ramas y pull requests.

## Primeros pasos

Sigue la [guía de instalación](../../docs/installation.es.md) y abre el repositorio del proyecto en Claude Code o Codex. Cada compañero que utilice la skill necesita tenerla instalada en su entorno o compartida mediante el directorio de skills del proyecto.

Proporciona los requisitos y los enlaces al repositorio de GitHub y al tablero de Trello que deseas utilizar. Conecta las cuentas con acceso a esos destinos. La skill utiliza las integraciones disponibles y puede recurrir a `gh` autenticado para GitHub. También admite trabajar solamente con GitHub, solamente con Trello para seguimiento, o con planificación y Git local.

Ejecuta `/team-workflow init` en Claude Code o `$team-workflow init` en Codex. La skill lee los archivos `AGENTS.md`, `CLAUDE.md` y `CONTRIBUTING.md` aplicables, las plantillas y las convenciones del proyecto. Se adapta a la rama de integración y a las listas reales de Trello, incluidas las etapas adicionales de revisión, QA o despliegue. Cuando falta una regla o un destino es ambiguo, pregunta por el dato necesario.

## Comandos

Antecede los comandos de la tabla con `/team-workflow` en Claude Code o `$team-workflow` en Codex.

| Comando | Ejemplo en Claude Code | Resultado |
| --- | --- | --- |
| `init` | `/team-workflow init` | Identifica el proyecto, el equipo, las herramientas y las reglas de trabajo. |
| `plan` | `/team-workflow plan` | Propone tareas, criterios de aceptación, dependencias y responsables. |
| `sync [tarea]` | `/team-workflow sync E1-03` | Concilia tarjetas e issues autorizados e informa los registros afectados. |
| `start <tarea>` | `/team-workflow start E1-03` | Comprueba que la tarea puede iniciarse y crea o reutiliza su rama. |
| `pr [tarea]` | `/team-workflow pr E1-03` | Comprueba el trabajo y prepara o publica el PR según lo solicitado. |
| `status [tarea]` | `/team-workflow status` | Resume avances, evidencia, bloqueos y próximos pasos. |
| `close <tarea>` | `/team-workflow close E1-03` | Verifica la integración y actualiza los registros autorizados. |

`<tarea>` es obligatorio y `[tarea]` es opcional. Identifica una tarea con su ID existente o la URL de su tarjeta o issue. Por ejemplo, `E1-03` podría representar la tercera tarea de la primera épica. Identificadores como `TW-014` son convenciones ilustrativas. Utiliza la identificación acordada por el equipo. La skill pregunta cuando la referencia es ambigua.

## Ejemplo de proyecto paso a paso

Supongamos que tres compañeros deben construir una aplicación de reservas. Tienen un repositorio de GitHub, un tablero de Trello y requisitos escritos. La rama de integración es `develop` y el tablero tiene Backlog, Ready, In progress, Code review, QA y Done. Los ejemplos siguientes utilizan Claude Code. En Codex, sustituye `/team-workflow` por `$team-workflow`.

1. **Establecer el contexto.** Ejecuta `/team-workflow init` y proporciona los requisitos, los enlaces al repositorio y tablero, y los datos del equipo que falten. La skill lee las reglas existentes e identifica la rama de integración, los destinos verificados, la correspondencia de etapas y las condiciones de cierre. El equipo puede pedirle que guarde la configuración acordada para sesiones futuras.

2. **Acordar las tareas.** Ejecuta `/team-workflow plan`. La skill propone tareas para crear reservas, consultar disponibilidad y cancelar, con criterios de aceptación y dependencias. El equipo revisa los responsables y el esfuerzo propuestos y ajusta el plan. En este ejemplo, `E1-03` es la cancelación y depende de que exista la creación de reservas.

3. **Publicar el plan acordado.** Autoriza las tareas y asignaciones concretas en el tablero y repositorio seleccionados y ejecuta `/team-workflow sync`. La skill crea o reutiliza tarjetas e issues, conserva su identificación común y añade enlaces recíprocos. Repetir `sync` en el mismo estado reutiliza esos registros. Si una interrupción dejó actualizado un solo sistema, la skill informa lo que logró y retoma desde los registros confirmados.

4. **Iniciar una tarea preparada.** Una vez integrada la creación de reservas, el responsable ejecuta `/team-workflow start E1-03`. La skill comprueba los criterios y la evidencia de la dependencia y prepara una rama desde `develop` según las reglas de nombres del repositorio. Con autorización para actualizar Trello, mueve la tarjeta a In progress e informa la rama y el enlace. Un worktree separado permite conservar cambios locales ajenos a la tarea.

5. **Implementar y comprobar.** Pide al agente que implemente la cancelación y ejecute las pruebas pertinentes. Al solicitar un commit, la skill sigue las reglas de Conventional Commits del proyecto, por ejemplo `feat(bookings): support cancellation`. Informa qué comprobaciones se ejecutaron y sus resultados. La implementación puede solicitarse después de preparar la tarea.

6. **Preparar y publicar el PR.** Ejecuta `/team-workflow pr E1-03` e indica si deseas preparar la propuesta o publicarla. Para una publicación autorizada, la skill verifica el trabajo, sube la rama según lo autorizado, crea o reutiliza el PR hacia `develop` y lo enlaza con la tarea. Informa los checks pendientes o fallidos. Puede mover la tarjeta a Code review y solicitar revisores aptos dentro de la autorización recibida.

7. **Revisar, probar e integrar.** Un compañero revisa el PR, pudiendo utilizar `review-pr` si está instalada. El autor responde a los cambios solicitados en la misma rama. El equipo sigue sus reglas de Code review y QA antes de integrar. Solicita las transiciones acordadas en Trello durante ese trabajo. Las aprobaciones independientes exigidas y la evidencia de QA forman parte de los criterios de finalización.

8. **Verificar y registrar el cierre.** Después de la integración, ejecuta `/team-workflow close E1-03` y autoriza las actualizaciones correspondientes. La skill comprueba el PR integrado, su SHA de integración, los criterios de aceptación y las revisiones y checks exigidos. Al cumplirse esas condiciones, registra la evidencia, mueve la tarjeta a Done y cierra el issue según corresponda. Si falta alguna condición, informa el trabajo pendiente antes de actualizar los registros.

9. **Consultar el avance durante el proyecto.** Ejecuta `/team-workflow status` para una visión general o `/team-workflow status E1-03` para una tarea. El informe identifica trabajo en curso, dependencias bloqueadas, PRs y revisiones o comprobaciones pendientes, con enlaces a la evidencia.

## Autorización y resultados confirmados

El descubrimiento, la planificación y los informes de estado son de lectura por defecto. La skill presenta las tarjetas, issues y asignaciones propuestos antes de aplicarlos. Una aprobación ya otorgada para acciones y destinos concretos sigue vigente dentro de ese alcance. Solicitar una rama local autoriza su preparación. Los pushes y cambios en los registros también requieren una autorización aplicable.

La skill confirma los cambios remotos antes de informar que se realizaron y entrega enlaces a los registros afectados. Cuando falta acceso o una operación se completa parcialmente, informa el resultado y el paso pendiente.

El mantenedor confirma el uso satisfactorio de esta skill en proyectos reales. La validación adicional incluye un recorrido con GitHub y Trello reales. Consulta los [escenarios de validación](tests/scenarios.md) para revisar casos simulados y recuperación de operaciones interrumpidas.
