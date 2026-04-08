# Especialidades Futuras

Estructura preparada para definir subagentes, skills o roles especializados cuando hagan falta.

---

## Filosofía
No crear especialidades por moda ni por simetría artificial.
Una especialidad solo debe existir si resuelve un problema real que las instrucciones generales (AGENTS.md / CLAUDE.md) no cubren bien.

## Cuándo crear una especialidad
- Cuando una tarea recurrente requiere un protocolo específico que no encaja en las reglas generales
- Cuando un tipo de revisión necesita contexto especializado (ej: seguridad, accesibilidad, performance)
- Cuando un flujo se beneficia de un agente con scope limitado y outputs definidos

## Cuándo NO crear una especialidad
- Para resolver algo que se necesita una sola vez
- Para imponer un gate burocrático sin valor real
- Para tener "más agentes" sin una necesidad concreta
- Para replicar lo que ya hacen AGENTS.md o CLAUDE.md

## Cómo crear una especialidad
1. Copiar `_template-especialidad.md`
2. Nombrar descriptivamente: `reviewer-seguridad.md`, `governor-diseno.md`, etc.
3. Completar todas las secciones
4. Decidir si se implementa como:
   - Subagente de Claude (en `.claude/agents/`)
   - Skill de Claude
   - Instrucción adicional para Codex (sección en AGENTS.md)
   - Documentación neutral (protocolo que ambas herramientas siguen)

## Preguntas para definir especialidades

Antes de crear una especialidad, responder:

1. **¿Qué problema concreto resuelve?** (no qué "rol" llena)
2. **¿Con qué frecuencia se necesita?** (cada cambio, cambios grandes, bajo demanda)
3. **¿Para qué herramienta?** (Claude, Codex, ambas, neutral)
4. **¿Qué debe leer antes de actuar?**
5. **¿Qué debe producir?**
6. **¿Qué NO debe hacer?**
7. **¿Qué pasa si no existe?** (si la respuesta es "nada grave", probablemente no hace falta)

## Especialidades definidas

| Nombre | Tipo | Propósito | Estado |
|--------|------|-----------|--------|
| framework-sanitizer | Neutral + Claude agent + Codex skill | Sanear drift documental del repo base y mantener README/QA/changelog alineados | Activa |

## Invocación rápida

- Codex: `Usa la skill framework-sanitizer y sanea el repo base`
- Claude: `Usa framework-sanitizer para revisar drift del repo base`

Fuente de verdad de esta especialidad:
- `docs/especialidades/framework-sanitizer.md`
