---
name: sop-builder
description: >
  Construye procedimientos operativos estándar (SOPs) que documentan un proceso paso a paso para
  consistencia, capacitación y delegación — tanto como entregable para empresas cliente de Strategic IA
  como para estandarizar procesos internos. Aplica rigor RFC 2119 (DEBE / DEBERÍA / PUEDE),
  parámetros reutilizables, RACI y control de versiones, y entrega en .docx con branding del cliente
  o neutro. Usar cuando el usuario dice "documentar este proceso", "armar un SOP", "procedimiento
  operativo", "manual de procedimiento", "estandarizar cómo hacemos X", "POE", "instructivo de
  trabajo", "que el equipo lo pueda seguir sin mí", o cuando hay que convertir un proceso informal en
  documentación operativa repetible. NO usar para descripciones de puesto (eso es descripcion-puesto)
  ni para diseñar la automatización técnica del proceso (eso es crm-automation-setup) — el SOP
  documenta el procedimiento, no construye el workflow.
allowed-tools: Read, Write, Bash, Skill
---

# SOP Builder — procedimientos operativos estándar

Tu misión es transformar un proceso (informal, en la cabeza de alguien, o disperso) en un **SOP claro, accionable y repetible** que cualquiera del equipo pueda seguir sin supervisión. Un SOP no limita libertad: la libera, al eliminar las decisiones rutinarias para que el equipo piense en lo que importa.

Método base: `agent-sop` (Apache 2.0) — rigor RFC 2119, parámetros, estructura canónica — sobre el `constructor-sop` del bundle, con la capa Strategic IA (RACI, versionado, branding, salida docx).

## Paso 0 — Encuadre (antes de escribir nada)

Definí dos cosas y recolectá el proceso:

1. **Ámbito** — determina branding y tono:
   - **Cliente** (entregable de consultoría): branding del cliente desde `C:/claude/<slug>/branding/`, tono profesional adaptado al país (voseo solo AR/UY). Si el proceso es de un cliente con pipeline cargado, podés leer `modelo-negocio`/`perla-diagnostic` para entender contexto antes de entrevistar.
   - **Interno Strategic IA**: documento operativo neutro, sin branding de cliente (cómo corrés pipelines, deploys, onboarding de clientes, etc.).
2. **Recolección del proceso** — entrevistá al dueño del proceso una pregunta a la vez: ¿qué dispara el proceso?, ¿quién hace qué?, ¿cuáles son los pasos reales (no los ideales)?, ¿dónde se traba o falla?, ¿qué decisiones hay que tomar y con qué criterio?, ¿qué registro queda? Si la respuesta es vaga, repreguntá. No inventes pasos.
3. **Parámetros** — identificá qué varía entre ejecuciones (cliente, monto, canal, turno) → eso son parámetros del SOP, no valores hardcodeados.

## Estructura canónica del SOP (plantilla a producir)

ALWAYS usar esta estructura. Cada SOP es un documento autocontenido.

```
# SOP: [Nombre del proceso]

| Campo | Valor |
|---|---|
| Propósito | Por qué existe este proceso (1-2 líneas) |
| Dueño del proceso | Rol responsable (no nombre propio, salvo interno) |
| Ámbito | Interno / Cliente: [empresa] |
| Versión | v1.0 |
| Fecha | [YYYY-MM-DD] |
| Próxima revisión | [YYYY-MM-DD] |

## 1. Alcance
Qué incluye y qué EXCLUYE explícitamente. Los límites evitan zona gris.

## 2. Roles y responsabilidades (RACI)
| Actividad | Responsable (R) | Aprueba (A) | Consultado (C) | Informado (I) |
|---|---|---|---|---|
| [actividad] | [rol] | [rol] | [rol] | [rol] |

## 3. Insumos / parámetros
- **Requeridos:** [parámetro] — [qué es]
- **Opcionales:** [parámetro] — [default]
- **Herramientas/accesos:** [sistemas, permisos]

## 4. Procedimiento paso a paso
1. [Acción concreta en imperativo].
   - **Control:** [cómo se verifica que el paso quedó bien].
   - Si [condición], entonces [acción].
2. [Paso siguiente]…

## 5. Decisiones clave
| Situación | Acción | Quién decide |
|---|---|---|
| Si pasa X | Hacé Y | [rol] |

## 6. Checklist de verificación
- [ ] [verificación]
- [ ] [verificación]

## 7. Problemas comunes
| Problema | Causa probable | Solución |
|---|---|---|

## 8. Registros / evidencia
Qué queda documentado y dónde (planilla, CRM, carpeta).

## 9. Control de versiones
| Versión | Fecha | Cambio | Autor |
|---|---|---|---|
| v1.0 | [fecha] | Versión inicial | [autor] |
```

## Reglas de redacción

- **RFC 2119 en español** para fijar obligatoriedad sin ambigüedad:
  - **DEBE** = obligatorio · **NO DEBE** = prohibido · **DEBERÍA** = recomendado (se puede omitir con justificación) · **PUEDE** = opcional.
  - Ej: *"El operador DEBE verificar el stock antes de confirmar. DEBERÍA avisar al cliente si hay demora. PUEDE ofrecer un sustituto."*
- **Palabras simples, sin jerga.** Lo escribe quien ejecuta, no quien diseña.
- **Pasos en imperativo y atómicos** — una acción por paso. Si un paso tiene "y", probablemente son dos.
- **Cubrí las excepciones** — todo "¿y si pasa X?" va en Decisiones clave o Problemas comunes. Un SOP que solo cubre el caso feliz no sirve.
- **Cada paso lleva su control** — cómo sabe el que ejecuta que lo hizo bien. Sin control, no es estandarización.
- Diagramas/screenshots valen más que mil palabras: indicá dónde insertarlos `[insertar captura: ...]`.

## Modos de ejecución

- **Interactivo** (default): presentás la estructura, validás el proceso con el dueño en checkpoints, iterás antes de generar el documento final.
- **Auto**: si el proceso ya está claro y documentado, generás el SOP completo de una y lo presentás para revisión.

## Salida

1. Generá el SOP final en **`.docx`** vía el skill `docx`, con branding del cliente (paleta/tipografía/logo de `C:/claude/<slug>/branding/`) si es entregable, o neutro si es interno. Respetá la regla: Word con branding del cliente por defecto, salvo orden de borrador neutro.
2. Guardá también una copia legible (`.md`) en la carpeta correspondiente: cliente → `C:/claude/<slug>/<modulo-procesos>/`; interno → donde corresponda al proceso.
3. Abrí el archivo generado al terminar.

## Encadenamiento (handoff)

- **Antes:** si el proceso es de un cliente y no está claro, leer `modelo-negocio` / `perla-diagnostic` para contexto, o entrevistar al dueño del proceso.
- **Después:** si el proceso se va a **automatizar** (WhatsApp/CRM/IA), el SOP es el insumo — derivar a `crm-automation-setup` o a las skills de automatización de WhatsApp (Kapso). El SOP define el "qué y cómo manual"; la automatización lo ejecuta.

## Salvaguardas

- No inventes pasos ni datos del proceso: si falta información, preguntá al dueño.
- Documentá el proceso **real**, no el ideal — un SOP que nadie sigue porque no refleja la práctica es papel muerto.
- Marcá supuestos que requieran validación del dueño antes de publicar la v1.0.
