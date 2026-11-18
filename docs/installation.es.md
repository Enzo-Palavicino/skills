# Instalación

[English](installation.md) · Español

## Descargar el catálogo

Ejecuta estos comandos en la terminal desde la carpeta donde guardas tus repositorios.

```bash
git clone https://github.com/Enzo-Palavicino/skills.git
cd skills
```

Cada carpeta de skill debe contener su archivo `SKILL.md` antes de instalarse. Copia la carpeta completa para incluir referencias y plantillas.

## Instalar en un proyecto

Ejecuta el siguiente bloque desde la raíz del catálogo clonado. Sustituye `project_dir` por la ruta absoluta al proyecto de software donde utilizarás las skills. Usa `.claude` en `tool_dir` para Claude Code o `.agents` para Codex. Si utilizas ambos agentes, ejecútalo una vez para cada uno.

```bash
(
  set -eu
  project_dir="/ruta/absoluta/a/tu/proyecto"
  tool_dir=".claude"
  test -d "$project_dir"

  for skill in review-pr team-workflow; do
    test -f "skills/$skill/SKILL.md"
    destination="$project_dir/$tool_dir/skills/$skill"
    if [ -e "$destination" ] || [ -L "$destination" ]; then
      echo "Ya existe $destination. Revisa la instalación antes de actualizar."
      exit 1
    fi
  done

  mkdir -p "$project_dir/$tool_dir/skills"
  for skill in review-pr team-workflow; do
    cp -R "skills/$skill" "$project_dir/$tool_dir/skills/"
  done
)
```

Al incluir los directorios de skills en los commits del proyecto, los compañeros que lo clonen recibirán esas versiones, según las reglas del repositorio.

## Instalar para tu usuario

Desde la raíz del catálogo, utiliza las mismas comprobaciones con una ubicación personal. Elige `~/.claude/skills` para Claude Code o `~/.agents/skills` para Codex.

```bash
(
  set -eu
  install_dir="$HOME/.claude/skills"
  for skill in review-pr team-workflow; do
    test -f "skills/$skill/SKILL.md"
    destination="$install_dir/$skill"
    if [ -e "$destination" ] || [ -L "$destination" ]; then
      echo "Ya existe $destination. Revisa la instalación antes de actualizar."
      exit 1
    fi
  done
  mkdir -p "$install_dir"
  for skill in review-pr team-workflow; do
    cp -R "skills/$skill" "$install_dir/"
  done
)
```

## Invocar desde tu proyecto

Abre una sesión en la carpeta del proyecto de destino. Inicia Claude Code con `claude` o abre el proyecto en Codex. Escribe lo siguiente en la conversación del agente.

| Agente | Inicializar el proyecto | Revisar un PR |
| --- | --- | --- |
| Claude Code | `/team-workflow init` | `/review-pr 94` |
| Codex | `$team-workflow init` | `$review-pr 94` |

El número de PR corresponde al repositorio de GitHub de ese proyecto. También puedes utilizar la URL completa del PR. Si una skill recién instalada aún aparece ausente, abre una sesión nueva del agente en ese proyecto.

## Conexiones, actualizaciones y desinstalación

Conecta GitHub y Trello en cada agente según lo necesites. `gh` autenticado puede cubrir capacidades de GitHub que falten. Confirma el repositorio o tablero de destino al autorizar cambios externos.

Las copias conservan la revisión instalada. Para actualizar, descarga la revisión deseada del catálogo, compárala con la copia instalada, conserva los cambios propios del proyecto y reemplázala de forma deliberada. Para desinstalar, elimina el directorio específico de la skill de la ubicación donde la instalaste.

[Skills de Codex](https://learn.chatgpt.com/docs/build-skills) · [Skills de Claude Code](https://code.claude.com/docs/en/skills)
