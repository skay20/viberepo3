# PRD.md — Manifiesto Operativo

Este archivo ya no es el contenedor principal del PRD completo.
Su función es declarar **qué PRD está activo**, dónde está su snapshot y qué nivel de ejecución aplicar.

> Contrato aplicable: `docs/operacion/fuente-prd.md`

---

## Fuente PRD activa

- **Origen declarado por prompt:** `(completar)`  
  Ejemplo: `/Users/.../PROJECT_BIBLE.md` o URL o adjunto
- **Última ingesta:** `YYYY-MM-DD HH:MM`
- **Snapshot en repo:** `docs/contexto/prd-fuentes/(archivo).md`
- **Estado de validez:** `Activo` | `Reemplazado` | `Pendiente de ingesta`

## Tier de ejecución
Completar al inicio del proyecto o de cada tarea significativa.
Sin tier definido, asumir `standard`.

- **Nivel:** `lean` | `standard` | `strict`
- **Criterio de selección:**
  - `lean` — copy, estilos, typos, refactor local sin impacto funcional
  - `standard` — nueva feature, cambio de lógica, nueva ruta, UI nueva
  - `strict` — auth, schema de DB, dependencias críticas, cambios arquitectónicos, seguridad
- **Qué activa cada tier:** ver AGENTS.md o CLAUDE.md

## Resumen estructurado del PRD activo (opcional, breve)

- **Visión:** ...
- **Alcance inicial:** ...
- **Requisitos críticos:** ...
- **Restricciones críticas:** ...
- **Riesgos críticos:** ...

> Este resumen no reemplaza al PRD completo; solo acelera contexto.

## Registro de ingestas PRD

| Fecha | Fuente original | Snapshot | Ingerido por | Notas |
|------|------------------|----------|--------------|-------|
| YYYY-MM-DD HH:MM | ... | `docs/contexto/prd-fuentes/...` | Codex/Claude | ... |

## Reglas de uso

1. Al iniciar proyecto o tarea grande, el usuario debe indicar fuente explícita del PRD en el prompt.
2. El agente resuelve la fuente, crea snapshot en `docs/contexto/prd-fuentes/` y actualiza este manifiesto.
3. Si no hay fuente explícita válida al inicio, se bloquea ejecución y se solicita la referencia.
4. Cambios posteriores no se escriben en el PRD fundacional: se registran en `docs/cambios/`.
5. Si necesitás una plantilla editable de PRD completo, usar `PRD-template.md`.
