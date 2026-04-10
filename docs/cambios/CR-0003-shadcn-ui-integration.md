# [CR-0003] Integracion inicial de shadcn/ui en intake form

## Tipo
Change Request

## Fecha
2026-04-09

## Motivacion
Mejorar la UI de forma rápida, ordenada y reusable integrando `shadcn/ui` sin romper la lógica existente del formulario.

## Estado actual
La app usa React + Vite + Tailwind y componentes propios para botones, campos y tarjetas visuales.

## Comportamiento deseado
Contar con una base reusable de `shadcn/ui` y una primera mejora visible en la pantalla principal del flujo.

## Alcance e impacto

### Area funcional afectada
- Presentacion visual del formulario y bloques informativos

### Area tecnica afectada
- `product/intake-form/src/components/ui/*`
- `product/intake-form/src/components/Button.jsx`
- `product/intake-form/src/components/Field.jsx`
- `product/intake-form/src/App.jsx`
- `product/intake-form/src/index.css`
- `product/intake-form/vite.config.js`

### Impacto visual (si aplica)
- Componentes afectados: `button`, `card`, `input`
- ¿Rompe o extiende el design system?: Extiende el design system y establece `shadcn/ui` como nueva base reusable

## Supuestos
- La migracion debe ser incremental, manteniendo layout y lógica del flujo.
- Se prioriza compatibilidad con Tailwind 3 actual del repo.

## Riesgos
- El CLI actual de `shadcn/ui` genera piezas pensadas para Tailwind 4; se mitigó con adaptación manual a este stack.

## Decisiones relacionadas
- Complementa ADR: [0005] Adoptar shadcn/ui como base de componentes reutilizables

## Estado de implementacion
Implementado

## Verificacion realizada
- [x] `npm run lint`
- [x] `npm run build`

## Follow-ups
- Migrar más bloques a primitives de `shadcn/ui` si el proyecto crece.
- Evaluar una futura migracion a Tailwind 4 si se quiere usar el output del CLI sin adaptación.
