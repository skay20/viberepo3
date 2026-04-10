# Decisiones del Proyecto

Sistema de memoria persistente basado en ADRs (Architecture Decision Records).

## Propósito
Registrar toda decisión importante para que no se repitan errores, no se contradigan decisiones previas y el contexto no se pierda entre sesiones.

## Qué registrar
- Decisiones técnicas (stack, librerías, patrones)
- Decisiones de producto (alcance, prioridades, trade-offs)
- Supuestos adoptados cuando falta información
- Cosas explícitamente descartadas y por qué

> **Nota:** Las decisiones específicas de diseño visual (excepciones al design system, patrones nuevos de UI) van en `docs/diseno/decisiones/`, no aquí.

## Cómo crear una decisión
1. Copiar `_template-adr.md`
2. Nombrar como `NNNN-slug-descriptivo.md` (siguiente número disponible)
3. Completar todas las secciones
4. Registrar estado como "Aceptada" cuando esté confirmada

## Reglas
- Las decisiones son append-only: nunca se edita una decisión aceptada
- Para cambiar una decisión, crear una nueva que la reemplace y marcar la anterior como "Reemplazada por NNNN"
- Antes de tomar una decisión nueva, revisar las existentes para no contradecirlas
- Si una nueva decisión contradice una anterior, debe ser explícito y documentado

## Índice de decisiones

| # | Título | Estado | Fecha |
|---|--------|--------|-------|
| 0001 | [Adoptar VibeRepo como base de proyecto](0001-adoptar-vibeRepo.md) | Aceptada | 2026-04-06 |
| 0002 | [Convención de carpeta product/ para implementación](0002-convencion-carpeta-product.md) | Aceptada | 2026-04-07 |
| 0003 | [PRD por referencia con snapshot versionado](0003-prd-por-referencia-con-snapshot.md) | Aceptada | 2026-04-08 |
| 0004 | [Stack React + Vite + Tailwind para feature intake-form](0004-stack-react-vite-tailwind-intake.md) | Aceptada | 2026-04-08 |
| 0005 | [Adoptar shadcn/ui como base de componentes reutilizables](0005-adoptar-shadcn-ui-en-vite.md) | Aceptada | 2026-04-09 |
| 0006 | [Adoptar DESIGN.md como direccion visual activa para intake form](0006-adoptar-design-md-como-direccion-visual-activa.md) | Aceptada | 2026-04-10 |
