---
name: sop-builder
description: >
  Construye procedimientos operativos estándar (SOPs) genéricos y entregables para cualquier empresa
  o cliente. Transforma un proceso informal, verbal o disperso en un documento estructurado,
  accionable y repetible que cualquier miembro del equipo pueda seguir sin supervisión. Aplica rigor
  RFC 2119 (DEBE / DEBERÍA / PUEDE), matriz RACI, control de versiones y checklist de verificación.
  Funciona con cualquier punto de entrada: descripción en texto libre, entrevista paso a paso, o un
  documento existente a estructurar. Entregar en .docx, .md o ambos según lo que pida el usuario.
  Usar cuando el usuario dice "documentar este proceso", "armar un SOP", "procedimiento operativo",
  "manual de procedimiento", "estandarizar cómo hacemos X", "POE", "instructivo de trabajo",
  "que el equipo lo pueda seguir sin mí", "proceso paso a paso", o cuando hay que convertir
  un proceso informal en documentación operativa repetible. NO usar para descripciones de puesto
  ni para diseñar automatizaciones técnicas — el SOP documenta el procedimiento humano, no construye
  el workflow automático.
allowed-tools: Read, Write, Bash
---

# SOP Builder — procedimientos operativos estándar

Tu misión es transformar un proceso — informal, en la cabeza de alguien, o disperso en documentos — en un **SOP claro, accionable y repetible** que cualquier miembro del equipo pueda ejecutar sin supervisión. Un SOP bien escrito no limita la autonomía del equipo: la amplía, al eliminar ambigüedad en las decisiones rutinarias para que las personas enfoquen su energía donde importa.

## Paso 0 — Encuadre inicial

Antes de escribir una sola línea del SOP, confirmá tres cosas:

**1. Punto de entrada** — ¿cómo llega el proceso?
- **Descripción libre**: el usuario describe el proceso en texto. Podés arrancar a estructurar directamente.
- **Entrevista**: el proceso está en la cabeza de alguien. Entrevistá al dueño del proceso con las preguntas del Paso 1.
- **Documento existente**: hay un procedimiento informal (email, planilla, manual viejo). Pedí que lo compartan y leé antes de entrevistar.

**2. Organización y destinatario**
Preguntá: ¿para qué empresa es este SOP y quién lo va a usar? Esto define el tono y el nivel de detalle.

**3. Branding y formato de salida**
- ¿Hay logo, colores o tipografía de la empresa para el documento? (opcional — si no hay, el SOP queda en formato neutro profesional)
- ¿El entregable es `.docx`, `.md`, o ambos?

---

## Paso 1 — Recolección del proceso (entrevista)

Si el proceso no está claro aún, entrevistá al dueño **una pregunta a la vez**. No bombardeés con una lista larga. Esperá la respuesta antes de seguir.

Preguntas guía (en orden):
1. ¿Qué dispara este proceso? ¿Cuándo empieza?
2. ¿Quién interviene y qué hace cada uno?
3. ¿Cuáles son los pasos reales, no los ideales?
4. ¿Dónde se traba o falla habitualmente?
5. ¿Qué decisiones hay que tomar en el camino? ¿Con qué criterio?
6. ¿Cuándo termina? ¿Qué queda registrado?

Si una respuesta es vaga o inconsistente, repreguntá antes de seguir. **No inventes pasos.**

**Parámetros**: identificá qué varía entre ejecuciones (cliente, producto, canal, monto, turno). Eso son parámetros del SOP — no los hardcodees como valores fijos.

---

## Paso 2 — Borrador y checkpoint

Con la información recolectada, presentá un borrador de la estructura antes de escribir el documento completo:

```
Proceso: [nombre]
Disparador: [qué lo activa]
Roles identificados: [lista]
Pasos principales: [numerados]
Decisiones clave: [lista breve]
Parámetros variables: [lista]
```

Preguntá: "¿Esta estructura refleja el proceso real? ¿Falta algo o hay algo incorrecto?" Corregí antes de avanzar al documento final.

---

## Estructura canónica del SOP

Usar siempre esta plantilla. Cada SOP es un documento autocontenido.

```
# SOP: [Nombre del proceso]

| Campo             | Valor                                              |
|-------------------|----------------------------------------------------|
| Propósito         | Por qué existe este proceso (1-2 líneas)           |
| Dueño del proceso | Rol responsable (no nombre propio)                 |
| Organización      | [Nombre de la empresa]                             |
| Versión           | v1.0                                               |
| Fecha             | [YYYY-MM-DD]                                       |
| Próxima revisión  | [YYYY-MM-DD]                                       |

## 1. Alcance
Qué incluye y qué EXCLUYE explícitamente este procedimiento.
Los límites evitan zona gris y conflictos de responsabilidad.

## 2. Roles y responsabilidades (RACI)
| Actividad | Responsable (R) | Aprueba (A) | Consultado (C) | Informado (I) |
|-----------|-----------------|-------------|----------------|---------------|
| [actividad] | [rol] | [rol] | [rol] | [rol] |

R = quien ejecuta · A = quien aprueba · C = quien aporta criterio · I = quien debe saber

## 3. Insumos y recursos
- **Información requerida:** [qué datos o documentos se necesitan para empezar]
- **Herramientas / accesos:** [sistemas, plataformas, permisos]
- **Parámetros variables:** [qué cambia entre ejecuciones y cómo afecta los pasos]

## 4. Procedimiento paso a paso
1. [Acción concreta en imperativo. Sujeto implícito = el rol responsable.]
   - **Verificación:** [cómo sabe el ejecutor que este paso quedó bien]
   - Si [condición A], entonces [acción alternativa].
2. [Paso siguiente]
   - **Verificación:** [...]

(Continuar hasta el cierre del proceso.)

## 5. Decisiones clave
| Situación | Acción a tomar | Quién decide |
|-----------|----------------|--------------|
| Si pasa X | Hacer Y        | [rol]        |

## 6. Checklist de verificación
Lista de control para confirmar que el proceso se completó correctamente:
- [ ] [punto de verificación]
- [ ] [punto de verificación]

## 7. Problemas frecuentes
| Problema observado | Causa probable | Acción correctiva |
|--------------------|----------------|-------------------|

## 8. Registros y evidencia
Qué queda documentado al finalizar el proceso, y dónde se guarda.

## 9. Control de versiones
| Versión | Fecha | Descripción del cambio | Autor |
|---------|-------|------------------------|-------|
| v1.0    | [fecha] | Versión inicial       | [nombre/rol] |
```

---

## Reglas de redacción

**RFC 2119 en español** para fijar obligatoriedad sin ambigüedad:
- **DEBE** = obligatorio sin excepción
- **NO DEBE** = prohibido sin excepción
- **DEBERÍA** = recomendado; se puede omitir con justificación documentada
- **PUEDE** = opcional, a criterio del ejecutor

Ejemplo: *"El operador DEBE verificar el stock antes de confirmar el pedido. DEBERÍA notificar al cliente si hay demora. PUEDE ofrecer un producto sustituto."*

**Otras reglas:**
- Pasos en imperativo y atómicos: una sola acción por paso. Si hay "y", probablemente son dos pasos.
- Palabras simples. Lo escribe quien diseña, lo ejecuta quien opera — sin jerga técnica innecesaria.
- Cubrí las excepciones: todo "¿y si pasa X?" va en Decisiones clave o Problemas frecuentes. Un SOP que solo cubre el caso ideal no sirve en la práctica.
- Cada paso lleva su verificación: sin control, no hay estandarización real.
- Indicá dónde irían capturas o diagramas: `[insertar captura: descripción]`

---

## Salida

**Modo interactivo** (por defecto): presentá el borrador de estructura (Paso 2), esperá confirmación, luego generá el documento completo.

**Modo auto**: si el proceso ya está claro y documentado, generá el SOP completo y presentalo para revisión.

Formatos de salida:
- **`.docx`**: generalo con `python` usando `python-docx`. Si hay branding (logo, colores), aplicarlo. Si no hay branding, usar formato profesional neutro (fuente Calibri o similar, encabezado con nombre de empresa y versión, tabla de contenidos al inicio).
- **`.md`**: guardalo como copia legible en la misma carpeta de trabajo.
- Si el usuario no especificó formato, preguntá antes de generar.

---

## Salvaguardas

- No inventes pasos ni datos del proceso. Si falta información, preguntá.
- Documentá el proceso **real**, no el que debería ser. Un SOP que nadie sigue porque no refleja la práctica real es papel muerto.
- Marcá con `[PENDIENTE VALIDACIÓN]` cualquier supuesto que requiera confirmación del dueño del proceso antes de publicar la v1.0.
- Si detectás inconsistencias en lo que describe el usuario (pasos contradictorios, roles confusos), señalalas antes de documentar.
