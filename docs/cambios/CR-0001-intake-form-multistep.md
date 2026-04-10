# [CR-0001] Multi-step Candidate Intake Form

## Tipo
Change Request

## Fecha
2026-04-08

## Motivación
Implementar el PRD fundacional activo para captar datos de candidatos en un flujo de 4 pasos con validaciones obligatorias y UX de alta completitud.

## Estado actual
No existe implementación funcional en `product/`.

## Comportamiento deseado
Disponer de una app frontend autocontenida en `product/intake-form/` con:
- Intro con CTA
- Formulario de 4 pasos
- Navegación Atrás/Siguiente con bloqueo por validaciones
- Confirmación final de envío
- UI responsive y consistente

## Alcance e impacto

### Área funcional afectada
- Intake de candidatos (frontend)

### Área técnica afectada
- Archivos: `product/intake-form/*`
- Módulos: App React, componentes UI base, configuración Tailwind

### Impacto visual (si aplica)
- Componentes afectados: `Button`, `Field`, `Stepper`
- ¿Rompe o extiende el design system?: Extiende e inicializa foundations del proyecto derivado

## Supuestos
- La validación avanzada se limita a email válido y números > 0 en campos numéricos.
- El envío es confirmación client-side (sin integración API en esta fase).

## Riesgos
- Validaciones demasiado estrictas pueden generar fricción en completitud.
- Sin persistencia externa, la recarga de página pierde datos.

## Decisiones relacionadas
- Complementa ADR: [0002] Convención de carpeta `product/`
- Complementa ADR: [0004] Stack UI React + Vite + Tailwind para intake form

## Estado de implementación
Implementado

## Verificación realizada
- [x] Build de producción ejecutado en `product/intake-form`
- [x] Lint ejecutado en `product/intake-form`
- [x] Flujo de navegación y validación verificado por revisión de código

## Follow-ups
- Agregar tests de integración del flujo multi-step.
- Evaluar persistencia temporal en `localStorage` si producto lo requiere.
