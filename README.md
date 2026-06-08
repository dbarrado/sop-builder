# SOP Builder — skill para Claude Code

Skill de [Claude Code](https://claude.com/claude-code) que construye **procedimientos operativos estándar (SOPs)**: documenta un proceso paso a paso para lograr consistencia, capacitación y delegación.

Aplica:

- **Rigor RFC 2119** (DEBE / DEBERÍA / PUEDE) para fijar obligatoriedad sin ambigüedad.
- **Parámetros reutilizables** en vez de valores hardcodeados.
- **Matriz RACI** de roles y responsabilidades.
- **Control de versiones** y próxima revisión.
- Entrega en **`.docx`** con branding del cliente o neutro.

Sirve tanto como entregable para empresas cliente como para estandarizar procesos internos.

## Cuándo se activa

Cuando le pedís a Claude cosas como: *"documentar este proceso"*, *"armar un SOP"*, *"procedimiento operativo"*, *"manual de procedimiento"*, *"estandarizar cómo hacemos X"*, *"POE"*, *"instructivo de trabajo"*, *"que el equipo lo pueda seguir sin mí"*.

## Instalación

Una skill de Claude Code es una carpeta con un `SKILL.md` adentro, ubicada en tu directorio de skills.

### Opción A — clonar e instalar (recomendada)

```bash
# 1. Cloná este repo en cualquier carpeta temporal
git clone https://github.com/dbarrado/sop-builder.git

# 2. Copiá la carpeta de la skill a tu directorio de skills personal
#    Linux / macOS:
cp -r sop-builder/sop-builder ~/.claude/skills/

#    Windows (PowerShell):
Copy-Item -Recurse sop-builder\sop-builder "$env:USERPROFILE\.claude\skills\"
```

### Opción B — descarga manual

1. Descargá el archivo [`sop-builder/SKILL.md`](sop-builder/SKILL.md).
2. Creá la carpeta `~/.claude/skills/sop-builder/` (en Windows: `%USERPROFILE%\.claude\skills\sop-builder\`).
3. Colocá el `SKILL.md` adentro.

### Nivel de instalación

- **Personal** (todos tus proyectos): `~/.claude/skills/sop-builder/SKILL.md`
- **Por proyecto** (compartida vía el repo del proyecto): `<proyecto>/.claude/skills/sop-builder/SKILL.md`

## Verificación

Abrí Claude Code y escribí `/` — la skill `sop-builder` debería aparecer en la lista. O simplemente pedile *"armemos un SOP de este proceso"* y debería activarse sola.

## Uso

Una vez instalada, decile a Claude el proceso a documentar y el ámbito (cliente o interno). La skill te entrevista una pregunta a la vez, valida el proceso real (no el ideal), y produce el SOP en `.docx`.

## Licencia

El método base toma `agent-sop` (Apache 2.0). Esta skill agrega la capa de RACI, versionado y salida `.docx`.
