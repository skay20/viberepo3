# Framework Changelog

Registro de cambios del **repo base VibeRepo** (framework/gobernanza).
No usar este archivo para cambios de producto de un repo derivado.

---

## [2026-04-08] Sanitizacion de README y estructura publicada

### Actualizado
- `README.md` para reflejar la estructura real del repo (`.claude/agents/`, `skills/`, `product/README.md`, ADR `0003` y `framework-sanitizer`)
- `CLAUDE.md` para alinear su seccion de estructura con los artefactos reales del repo base

### Impacto
- Se reduce drift entre la estructura documentada y la estructura real del framework
- La invocacion y ubicacion de `framework-sanitizer` quedan visibles en la documentacion principal

### Follow-ups
- Volver a correr `framework-sanitizer` despues de cualquier cambio que agregue o mueva artefactos del framework

## [2026-04-08] Skill de sanitizacion del framework base

### Creado
- Especialidad neutral `docs/especialidades/framework-sanitizer.md`
- Agente Claude `.claude/agents/framework-sanitizer.md`
- Skill Codex `skills/framework-sanitizer/SKILL.md`

### Actualizado
- `docs/especialidades/README.md` con la nueva especialidad activa
- `AGENTS.md` y `CLAUDE.md` para recomendar la invocacion del sanitizer en cambios de framework
- `docs/qa/checklist.md`, `docs/qa/README.md`, `docs/operacion/gate-release.md` y `docs/operacion/contrato-ejecucion.md` para corregir drift de changelog base/derivado

### Impacto
- El repo ya tiene una forma reusable de auditar y sanear drift documental del framework
- Se corrigen gaps reales de consistencia detectados despues de separar `FRAMEWORK_CHANGELOG.md` y `CHANGELOG.md`

### Follow-ups
- Ejecutar `framework-sanitizer` despues de cualquier cambio relevante en gobernanza del repo base

## [2026-04-08] PRD por referencia con ingesta documentada

### Creado
- Contrato común de fuente PRD: `docs/operacion/fuente-prd.md`
- Carpeta de snapshots PRD con convención: `docs/contexto/prd-fuentes/README.md`
- ADR `0003-prd-por-referencia-con-snapshot.md`

### Actualizado
- `PRD.md` redefinido como manifiesto operativo (fuente activa, última ingesta, snapshot, tier)
- Sincronización de `AGENTS.md` y `CLAUDE.md` para resolver fuente PRD desde prompt
- `README.md` con flujo recomendado "Ejecuta este PRD: <ruta|adjunto|url>"
- Restaurado `PRD-template.md` como plantilla opcional, no obligatoria
- Índice de decisiones en `docs/decisiones/README.md`

### Impacto
- Se elimina el copy/paste manual como flujo principal
- Codex y Claude operan con el mismo contrato de entrada PRD
- Se preserva trazabilidad sin sobreingeniería (snapshot + manifiesto)

### Follow-ups
- Aplicar esta convención en repos hijos ya inicializados desde versiones anteriores
- Validar en primer arranque real que el snapshot se registre en cada nuevo proyecto

## [2026-04-07] Mejora de gobernanza anti-skip y estructura

### Creado
- Contrato común Codex/Claude: `docs/operacion/contrato-ejecucion.md`
- Reglas obligatorias de cierre con etiqueta `ENTREGA COMPLETA` o `ENTREGA PARCIAL`
- Formato obligatorio de Matriz de cobertura PRD para tareas grandes o ejecución completa del PRD

### Actualizado
- Sincronización de reglas críticas en `AGENTS.md` y `CLAUDE.md`
- Política de estructura framework vs producto en `docs/arquitectura/README.md` (default `product/`)
- Plantilla `PRD-template.md` con sección de ubicación de implementación
- `docs/run/README.md` con ejemplos de comandos en `product/` y compatibilidad legado
- `docs/qa/checklist.md` con validaciones anti-skip y política de carpetas
- `README.md` con flujo de uso alineado a contrato y convención de estructura

### Impacto
- Se reduce el riesgo de entregas parciales silenciosas
- Se unifica el comportamiento esperado entre Codex y Claude
- Se evita mezclar framework/documentación con implementación de producto en raíz

### Follow-ups
- Aplicar este contrato en todos los repos hijos ya creados desde versiones anteriores de la plantilla

---

## [2026-04-06] Setup inicial

### Creado
- Estructura base del repositorio VibeRepo
- Sistema de gobernanza: AGENTS.md, CLAUDE.md, PRD.md
- Sistema de decisiones: docs/decisiones/ con ADRs
- Sistema de cambios: docs/cambios/ para evolución post-PRD
- Documentación de arquitectura, QA, diseño, run state y especialidades
- Plantillas reutilizables para ADRs, cambios, componentes y especialidades

### Impacto
- El repo queda listo para clonar e iniciar cualquier proyecto nuevo desde un PRD

### Follow-ups
- Definir especialidades/subagentes según necesidades reales del primer proyecto
- Completar PRD.md con el contenido del primer proyecto
- Completar docs/contexto/README.md con stack y entorno reales
