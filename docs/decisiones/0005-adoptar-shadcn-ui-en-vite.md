# [0005] Adoptar shadcn/ui como base de componentes reutilizables

## Estado
Aceptada

## Fecha
2026-04-09

## Contexto
La app `product/intake-form` ya contaba con React, Vite y Tailwind, pero varios bloques visuales se resolvían con componentes propios muy livianos. Se pidió integrar `shadcn/ui` para acelerar mejoras visuales manteniendo orden, reutilización y bajo riesgo funcional.

## Opciones consideradas

### Opción A: Mantener componentes propios y seguir iterando manualmente
- Ventajas: cero dependencias UI nuevas
- Desventajas: menor velocidad para evolucionar consistencia y patrones reutilizables

### Opción B: Integrar shadcn/ui sobre el setup actual
- Ventajas: componentes composables, alineación con Tailwind, adopción incremental
- Desventajas: el CLI actual genera piezas pensadas para stacks más nuevos y requiere adaptación en Tailwind 3

## Decisión
Se adopta `shadcn/ui` de forma incremental en `product/intake-form`, manteniendo Tailwind como capa de layout y ajustes finos.

La integración se hace con:
- CLI oficial para bootstrap inicial
- adaptación manual de componentes generados a compatibilidad con Vite + Tailwind 3
- migración progresiva de pantallas visibles en vez de una reescritura completa

## Consecuencias
- `button`, `card` e `input` pasan a existir como base reusable en `src/components/ui/`
- se agrega `components.json`, alias `@` y utilidades `src/lib/utils.js`
- futuras migraciones UI deberían reutilizar primero `src/components/ui/` antes de crear más primitives locales

## Área afectada
Frontend | Arquitectura UI

## Relación con otras decisiones
- Complementa: [0004] Stack React + Vite + Tailwind para feature intake-form
