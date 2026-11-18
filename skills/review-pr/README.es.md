# review-pr

[English](README.md) · Español

Revisa un pull request de GitHub, consulta CI y prepara una aprobación o solicitud de cambios formal. Sigue la [guía de instalación](../../docs/installation.es.md) y abre el agente desde el repositorio cuyo PR quieres revisar.

## Comandos

| Agente | Comando dentro de la conversación |
| --- | --- |
| Claude Code | `/review-pr 94` |
| Codex | `$review-pr 94` |

El número identifica un PR del repositorio actual. También puedes utilizar la URL completa de un PR. La skill utiliza la integración con GitHub disponible y puede recurrir a `gh` autenticado. Si falta acceso, puedes aportar un diff u otra evidencia y el resultado identificará lo que fue posible verificar.

## Flujo de uso

1. Invoca la skill con el PR que deseas revisar.
2. El agente consulta el contexto, las reglas aplicables del proyecto, el diff y CI. Presenta sus hallazgos, la revisión evaluada, un veredicto recomendado y el comentario propuesto.
3. Si autorizas publicar la propuesta, responde en la misma conversación con una instrucción explícita como «Publica esa solicitud de cambios en el PR #94».
4. Antes de enviar, el agente comprueba que el commit y la rama base corresponden a lo revisado. Si cambiaron, prepara una revisión nueva para que la autorices.
5. Tras publicar, verifica la revisión formal y devuelve su enlace. La publicación requiere una conexión que permita escribir revisiones vinculadas al commit evaluado.

## Veredictos y evidencia

La skill recomienda `APPROVE` o `REQUEST_CHANGES` según los defectos verificados. Puede devolver `BLOCKED` cuando la evidencia es insuficiente o `COMMENT_ONLY` cuando corresponde una observación consultiva. El resultado distingue CI, las pruebas que realmente se ejecutaron y las comprobaciones pendientes.

## Validación

Los [escenarios de validación](tests/scenarios.md) utilizan datos simulados de GitHub. La publicación en un PR real de tu proyecto requiere validación en su entorno y con sus permisos.
