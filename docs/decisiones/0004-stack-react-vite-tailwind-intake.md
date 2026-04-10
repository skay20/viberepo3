# [0004] Stack React + Vite + Tailwind para feature intake-form

## Estado
Aceptada

## Fecha
2026-04-08

## Contexto
El PRD activo requiere una feature frontend completa con navegación multi-step, validaciones en cliente, transiciones suaves y UI responsive en `product/intake-form/`. Se necesita una base liviana y rápida de iterar.

## Opciones consideradas

### Opción A: HTML/CSS/JS sin framework
- Ventajas: cero dependencias de framework
- Desventajas: mayor fricción para estado complejo y escalado de componentes

### Opción B: React + Vite + Tailwind
- Ventajas: estado declarativo claro para multi-step, toolchain rápido, sistema de estilos utilitario compatible con tokens
- Desventajas: dependencia de ecosistema Node y setup inicial

### Opción C: Next.js
- Ventajas: framework robusto para crecimiento
- Desventajas: sobrecosto para fase sin backend ni SSR

## Decisión
Se adopta `React + Vite + Tailwind CSS` en `product/intake-form/` para implementar la feature del PRD actual.

- React resuelve el estado de pasos y validaciones de forma simple.
- Vite minimiza complejidad de build para proyecto autocontenido.
- Tailwind permite consistencia visual basada en tokens sin CSS disperso.

## Consecuencias
- Comandos de desarrollo/build/lint se ejecutan dentro de `product/intake-form`.
- El sistema visual se define vía tokens CSS + extensiones de Tailwind.
- La fase actual queda sin backend ni persistencia externa, alineada al PRD.

## Área afectada
Arquitectura | Frontend

## Relación con otras decisiones
- Complementa: [0002] Convención de carpeta product/ para implementación
