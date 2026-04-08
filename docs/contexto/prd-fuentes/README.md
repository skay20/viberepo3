# PRD Fuentes

Esta carpeta guarda snapshots versionados del PRD activo para trazabilidad.
Objetivo: evitar copy/paste manual en `PRD.md` y mantener evidencia reproducible.

---

## Convención

- Un archivo por ingesta de PRD.
- Formato recomendado: `YYYY-MM-DD-HHMM-prd-<slug>.md`
- Contenido:
  - metadatos de origen
  - contenido completo del PRD ingerido

## Flujo mínimo

1. El usuario pasa referencia explícita del PRD en el prompt.
2. El agente resuelve la fuente.
3. El agente guarda snapshot en esta carpeta.
4. El agente actualiza `PRD.md` con:
   - fuente activa
   - fecha de última ingesta
   - snapshot asociado

## Notas

- Esta carpeta es append-only para preservar historia.
- Cambios de alcance posteriores al PRD fundacional se registran en `docs/cambios/`.
