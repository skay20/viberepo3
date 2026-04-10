# Changelog del Proyecto Derivado

Registro de cambios del proyecto activo (repo derivado).
No usar este archivo para cambios del repo base VibeRepo; esos van en `FRAMEWORK_CHANGELOG.md`.

---

## [2026-04-08] Implementación PRD: Multi-step Candidate Intake Form

### Cambios
- Ingesta de PRD desde `/Users/matiassouza/Desktop/Prds Creados/PRDsimple.md` con snapshot versionado.
- Implementación completa en `product/intake-form/` con React + Vite + Tailwind.
- Flujo UI: intro -> 4 pasos -> confirmación final.
- Validación obligatoria por campo, bloqueo de navegación y feedback de error.
- Indicador de progreso (stepper + barra), navegación `Atrás/Siguiente` y transición suave `240ms`.
- Definición de tokens visuales (color, tipografía, spacing, radius, shadow) y uso en código.
- Documentación de componentes base: `Button`, `Field`, `Stepper`.
- Registro de cambio en `docs/cambios/CR-0001-intake-form-multistep.md`.
- ADR 0004 para decisión de stack.

### Impacto
- Se crea la primera UI funcional del proyecto derivado.
- Se habilita base reusable para próximas features frontend.
- Se actualizan artefactos de gobernanza y ejecución operativa.

### Follow-ups
- Incorporar tests de integración para flujo multi-step.
- Evaluar persistencia en `localStorage` para recuperación tras refresh.

## [2026-04-08] Premium UI refresh con referencia UI UX Pro Max

### Cambios
- Investigación visual usando el repositorio `nextlevelbuilder/ui-ux-pro-max-skill`.
- Selección de dirección `Classic Elegant` en tipografía y `Luxury/Premium Brand` en color.
- Rediseño del layout principal hacia un lenguaje editorial-premium con acento oro y capas translúcidas controladas.
- Actualización de `Button`, `Field`, `Stepper`, tokens CSS y mapeo Tailwind.
- Registro de decisión visual en `docs/diseno/decisiones/premium-editorial-direction.md`.
- Registro del cambio en `docs/cambios/CR-0002-premium-ui-refresh.md`.

### Impacto
- La UI pasa de un lenguaje SaaS genérico a una presencia más alta gama y diferenciada.
- Se conserva el flujo funcional del PRD mientras mejora la percepción de calidad.

### Follow-ups
- Verificar visualmente el resultado en móvil real y desktop ancho.

## [2026-04-09] Integracion inicial de shadcn/ui

### Cambios
- Inicializacion de `shadcn/ui` en `product/intake-form` usando el CLI oficial con template Vite.
- Alta de `components.json`, alias `@`, `src/lib/utils.js` y primitives `button`, `card`, `input`.
- Adaptacion manual de los componentes generados para compatibilidad con Vite + Tailwind CSS 3.
- Sustitucion parcial de UI propia por base `shadcn/ui` en la pantalla principal del flujo.
- `Button.jsx` y `Field.jsx` pasan a usar `shadcn/ui` por debajo.

### Impacto
- La app gana una base reusable y mas ordenada para evolucion UI incremental.
- La mejora visible se concentra en la pantalla del formulario sin alterar logica de negocio.

### Follow-ups
- Migrar mas primitives locales a `src/components/ui/` si se amplía la app.
- Evaluar migracion futura a Tailwind 4 si se quiere alineacion total con el output actual del CLI.
