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

## [2026-04-10] Pasada visual guiada por DESIGN.md adaptado desde ElevenLabs

### Cambios
- Uso explícito de `product/intake-form/DESIGN.md` como referencia visual activa para el producto.
- Revisión del shell principal con chrome oscuro exterior y paneles internos claros para elevar contraste y jerarquía.
- Ajuste de tokens de color, sombras, radius y estados en `src/index.css` y `tailwind.config.js`.
- Refinamiento de `Button`, `Field`, `Stepper`, `Card` e `Input` para una presencia más técnica y sobria.
- Actualización de `AGENTS.md` y `CLAUDE.md` para exigir lectura de `DESIGN.md` en tareas de UI cuando exista una guía aplicable.
- Registro de la nueva decisión visual en `docs/diseno/decisiones/elevenlabs-adapted-product-direction.md`.
- ADR 0006 para formalizar `DESIGN.md` como nueva referencia visual activa.
- Registro del cambio en `docs/cambios/CR-0004-design-md-visual-pass.md`.

### Impacto
- La UI mantiene el flujo y la lógica existentes, pero gana un lenguaje visual más moderno, limpio y reusable.
- Se alinea la gobernanza del repo con una fuente visual explícita para futuras iteraciones de UI.

### Follow-ups
- Validar la interfaz en móvil real y desktop ancho.
- Extender esta dirección a nuevas pantallas si el producto crece.

## [2026-04-10] Ajuste de gobernanza documental al estado real del repo

### Cambios
- Actualización del `README.md` raíz para reflejar que este repositorio opera hoy como proyecto derivado y no solo como plantilla.
- Alineación de `docs/contexto/README.md`, `docs/run/README.md` y `product/README.md` con el producto activo en `product/intake-form`.
- Adición de referencias explícitas a `product/intake-form/DESIGN.md` como guía visual activa y a los documentos canónicos vigentes.

### Impacto
- Se reduce la ambigüedad entre documentación de plantilla base y realidad operativa del repo actual.
- La navegación documental queda más clara para humanos y agentes.

### Follow-ups
- Si el repo vuelve a usarse como framework puro, separar mejor la documentación de plantilla del estado del proyecto derivado.
