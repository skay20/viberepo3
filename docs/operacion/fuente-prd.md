# Contrato de Fuente PRD

Contrato operativo comun para Codex y Claude para iniciar trabajo desde un PRD referenciado, sin copy/paste manual en `PRD.md`.

---

## Objetivo

- Permitir arrancar desde una referencia de PRD (ruta, adjunto o URL).
- Mantener trazabilidad con bajo overhead.
- Estandarizar el comportamiento entre Codex y Claude.

## Entrada esperada

Se acepta lenguaje natural, siempre con referencia explicita del PRD.

Ejemplos validos:
- `Ejecuta este PRD: /ruta/absoluta/mi-prd.md`
- `Ejecuta este PRD: docs/input/PRD-FamilyTravel.md`
- `Ejecuta este PRD: [adjunto] PROJECT_BIBLE.md`
- `Ejecuta este PRD: https://.../prd.md`

## Regla de inicio (obligatoria)

1. Resolver primero la fuente PRD desde el prompt.
2. Si la referencia falta al iniciar proyecto o tarea grande, **no ejecutar implementación**.
3. En ese caso, pedir la referencia de PRD de forma explícita.

## Resolución de fuente

Orden de prioridad:
1. Referencia explícita en el prompt actual.
2. Si el prompt no trae referencia, usar la fuente activa declarada en `PRD.md` solo para tareas menores no fundacionales.
3. Si no hay fuente activa válida, bloquear y pedir referencia.

## Ingesta y trazabilidad

Cuando la referencia es válida, el agente debe:

1. Crear snapshot versionado en `docs/contexto/prd-fuentes/`.
2. Registrar metadatos mínimos:
   - origen (ruta, URL o adjunto)
   - fecha y hora
   - agente/herramienta
   - hash o identificador simple de contenido (si aplica)
3. Actualizar `PRD.md` (manifiesto) con:
   - fuente PRD activa
   - última ingesta
   - ruta del snapshot
4. Evitar pedir copy/paste manual del PRD salvo bloqueo real de acceso.

## Formato sugerido de snapshot

Nombre de archivo:
`YYYY-MM-DD-HHMM-prd-<slug>.md`

Cabecera mínima:
- `Fuente original: ...`
- `Fecha de ingesta: ...`
- `Ingerido por: ...`
- `Notas de alcance: ...`

Luego incluir el contenido completo del PRD.

## Reglas de consistencia

- `AGENTS.md` y `CLAUDE.md` deben referenciar este contrato sin contradicciones.
- `PRD.md` funciona como manifiesto de control del PRD activo.
- El PRD fundacional no se reescribe con cambios posteriores: esos van en `docs/cambios/`.
- Este contrato complementa, no reemplaza, `docs/operacion/contrato-ejecucion.md`.
