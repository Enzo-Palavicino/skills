# Repository governance

## English

Configuration verified on November 18, 2026, for `Enzo-Palavicino/skills`.

| Control | Applied configuration |
| --- | --- |
| Visibility | Public, with public read and clone access. |
| Direct collaborators | Only `Enzo-Palavicino`, with owner/admin access. |
| Pending invitations and deploy keys | None at verification time. |
| Issue and PR creation | Permanent `COLLABORATORS_ONLY` policies. With the current access list, this permits the owner. |
| Branches and tags | All refs restrict creation, update, and deletion to the owner through explicit user bypass. |
| `main` history | Force-push and deletion blocked for all actors. The owner can manage the rules in Settings. |
| Conversations | Temporary `collaborators_only` limit through May 18, 2027 at 15:33:07 UTC. |
| Wiki, Discussions, Projects | Disabled. |
| GitHub Actions | Read-only default token, PR review approval disabled, GitHub-owned actions allowed with full-SHA pinning required. |
| Secrets | Secret scanning and secret scanning push protection enabled. |

The branch and tag rulesets authorize the account that pushes or merges. The commit author field is Git metadata supplied by a client. Access controls govern who can publish changes to this repository.

The owner manages releases and repository settings through owner/admin permissions. `CODEOWNERS` records file ownership. The actual restrictions are applied in GitHub Settings.

Issue and PR creation restrictions persist until changed. GitHub's additional interaction limit expires automatically and needs renewal to keep comments and reactions restricted after that date. Review collaborator, app, token, and deploy-key permissions whenever granting access to a new tool.

The owner can renew the additional conversation limit from Settings → Moderation options → Interaction limits, or with authenticated GitHub CLI.

```bash
gh api --method PUT repos/Enzo-Palavicino/skills/interaction-limits \
  -f limit=collaborators_only -f expiry=six_months
```

Check the returned `expires_at` and update this record after renewal.

Public users can read, clone, fork, and reuse the code under its MIT License. These operations apply to public copies. Changes to the maintained repository use the owner-controlled access above.

[Issue creation policy](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/disabling-issues) · [PR creation policy](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/disabling-pull-requests) · [Rulesets](https://docs.github.com/en/rest/repos/rules) · [Temporary interaction limits](https://docs.github.com/en/communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository)

## Español

Configuración verificada el 18 de noviembre de 2026 para `Enzo-Palavicino/skills`.

| Control | Configuración aplicada |
| --- | --- |
| Visibilidad | Pública, con acceso de lectura y clonación. |
| Colaboradores directos | Únicamente `Enzo-Palavicino`, con acceso de propietario/administrador. |
| Invitaciones pendientes y deploy keys | Ninguna al verificar. |
| Creación de issues y PRs | Políticas permanentes `COLLABORATORS_ONLY`. Con los accesos actuales, permiten al propietario. |
| Ramas y etiquetas | Todos los refs restringen su creación, modificación y eliminación al propietario mediante una excepción explícita para su usuario. |
| Historial de `main` | Force-push y eliminación bloqueados para todos. El propietario puede administrar las reglas desde Settings. |
| Conversaciones | Límite temporal `collaborators_only` hasta el 18 de mayo de 2027 a las 15:33:07 UTC. |
| Wiki, Discussions y Projects | Deshabilitados. |
| GitHub Actions | Token de lectura por defecto, aprobación de revisiones deshabilitada y acciones de GitHub permitidas con fijación obligatoria a un SHA completo. |
| Secretos | Detección de secretos y protección de pushes habilitadas. |

Las reglas de ramas y etiquetas autorizan a la cuenta que hace el push o la integración. El campo de autor de un commit es un metadato de Git proporcionado por el cliente. Los controles de acceso determinan quién puede publicar cambios en este repositorio.

El propietario administra las publicaciones y la configuración mediante sus permisos de administración. `CODEOWNERS` registra la propiedad de los archivos. Las restricciones se aplican en Settings de GitHub.

Las restricciones de creación de issues y PRs permanecen vigentes hasta que se cambien. El límite adicional de interacción vence automáticamente y debe renovarse para mantener restringidos los comentarios y reacciones después de esa fecha. Revisa los permisos de colaboradores, aplicaciones, tokens y deploy keys al autorizar herramientas nuevas.

El propietario puede renovar el límite adicional de conversación desde Settings → Moderation options → Interaction limits, o mediante GitHub CLI autenticado con el comando de la sección en inglés. Comprueba el valor `expires_at` devuelto y actualiza este registro después de renovarlo.

Cualquier persona puede consultar, clonar, hacer un fork y reutilizar el contenido según su licencia MIT. Estas operaciones se realizan sobre copias públicas. Los cambios al repositorio mantenido utilizan los accesos controlados por el propietario descritos arriba.
