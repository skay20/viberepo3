# PRD.md — Manifiesto Operativo

Este archivo declara qué PRD está activo, dónde está su snapshot y qué nivel de ejecución aplicar.

> Contrato aplicable: `docs/operacion/fuente-prd.md`

---

## Fuente PRD activa

- **Origen declarado por prompt:** `/Users/matiassouza/Desktop/Prds Creados/PRDsimple.md`
- **Última ingesta:** `2026-04-08 14:14 CEST`
- **Snapshot en repo:** `docs/contexto/prd-fuentes/2026-04-08-1414-prd-multi-step-candidate-intake-form.md`
- **Estado de validez:** `Activo`

## Tier de ejecución

- **Nivel:** `standard`
- **Criterio de selección:** Nueva feature completa con UI, validación y navegación multi-step.

## Resumen estructurado del PRD activo

- **Visión:** Formulario de intake de candidatos en 4 pasos con UX moderna y progresiva.
- **Alcance inicial:** Intro, 4 pasos con navegación, validación obligatoria, animaciones y pantalla final.
- **Requisitos críticos:** Bloquear avance por campos requeridos, persistir estado en sesión, indicador de progreso, responsive.
- **Restricciones críticas:** Solo frontend, sin backend, sin persistencia externa, uso de Tailwind CSS.
- **Riesgos críticos:** Fricción por validaciones/UX y degradación de performance por animaciones.

## Registro de ingestas PRD

| Fecha | Fuente original | Snapshot | Ingerido por | Notas |
|------|------------------|----------|--------------|-------|
| 2026-04-08 14:14 | `/Users/matiassouza/Desktop/Prds Creados/PRDsimple.md` | `docs/contexto/prd-fuentes/2026-04-08-1414-prd-multi-step-candidate-intake-form.md` | Codex | Ingesta inicial para ejecutar feature completa multi-step intake form |

## Reglas de uso

1. Al iniciar proyecto o tarea grande, el usuario debe indicar fuente explícita del PRD en el prompt.
2. El agente resuelve la fuente, crea snapshot en `docs/contexto/prd-fuentes/` y actualiza este manifiesto.
3. Si no hay fuente explícita válida al inicio, se bloquea ejecución y se solicita la referencia.
4. Cambios posteriores no se escriben en el PRD fundacional: se registran en `docs/cambios/`.
5. Si necesitás una plantilla editable de PRD completo, usar `PRD-template.md`.
