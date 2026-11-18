# Skills

[English](README.md) · Español

Agent Skills reutilizables para Codex y Claude Code, mantenidas por Enzo Palavicino. Permiten revisar pull requests y coordinar el desarrollo de software siguiendo las reglas del proyecto y las herramientas disponibles para el agente.

## Catálogo de skills

| Skill | Propósito | Disponibilidad |
| --- | --- | --- |
| [review-pr](skills/review-pr/README.es.md) | Analizar un PR, su diff y CI, proponer un veredicto y publicar la revisión después de recibir autorización. | Funcional |
| [team-workflow](skills/team-workflow/README.es.md) | Conectar planificación, tarjetas de Trello, issues de GitHub, ramas, PRs y cierre de tareas. | Funcional |

Ambas skills son funcionales. El mantenedor confirma que utilizó Review PR y Team Workflow satisfactoriamente en proyectos reales. La validación adicional incluye escenarios simulados y un recorrido de Team Workflow con un repositorio privado de GitHub y un tablero de Trello. Ese proyecto de prueba carecía de checks de CI.

## Instalación y uso

Clona este repositorio y copia las carpetas completas de las skills en la ubicación personal del agente o en el directorio de skills del proyecto donde las usarás. La [guía de instalación](docs/installation.es.md) incluye comandos que comprueban si ya hay una instalación antes de copiar.

| Agente | Instalación personal | Instalación en un proyecto | Invocación dentro del agente |
| --- | --- | --- | --- |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | `/team-workflow init` o `/review-pr 94` |
| Codex | `~/.agents/skills/` | `.agents/skills/` | `$team-workflow init` o `$review-pr 94` |

Abre el agente desde el proyecto de software en el que trabajarás. Escribe el comando de la skill en la conversación del agente. Claude Code interpreta el comando con `/`. La terminal se utiliza para instalar las skills y abrir el agente.

GitHub CLI (`gh`) es una alternativa opcional. Las operaciones en GitHub y Trello dependen de las conexiones autenticadas y los permisos disponibles en el agente que utilices. Configura las conexiones de cuenta de cada agente en su entorno.

## Estructura del repositorio

```text
skills/
├── .github/
│   └── CODEOWNERS
├── docs/
│   ├── installation.md
│   ├── installation.es.md
│   ├── development.md
│   └── governance.md
├── skills/
│   ├── review-pr/
│   │   ├── SKILL.md
│   │   ├── references/
│   │   └── tests/
│   └── team-workflow/
│       ├── SKILL.md
│       ├── references/
│       ├── assets/
│       └── tests/
├── README.md
├── README.es.md
├── CONTRIBUTING.md
├── SECURITY.md
├── AGENTS.md
└── LICENSE
```

Cada skill sigue la [especificación de Agent Skills](https://agentskills.io/specification) y tiene un archivo `SKILL.md` como entrada. Los procedimientos de apoyo viven en `references/`, las plantillas reutilizables en `assets/` y los escenarios de comportamiento en `tests/`. Los README en inglés y español acompañan las instrucciones compartidas de cada skill.

## Mantenimiento y seguridad

Enzo Palavicino administra este repositorio y sus issues, PRs, ramas y publicaciones. Cualquier persona puede consultar e instalar las skills publicadas bajo la licencia MIT. Los permisos y las reglas de GitHub aplican la política de mantenimiento. Consulta los [detalles de administración](docs/governance.md#español), la [política de mantenimiento](CONTRIBUTING.md#español) y la [política de seguridad](SECURITY.md#español).

## Licencia

[MIT](LICENSE) · Copyright © 2026 Enzo Palavicino.
