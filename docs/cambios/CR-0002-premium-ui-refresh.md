# [CR-0002] Premium UI Refresh para intake form

## Tipo
Change Request

## Fecha
2026-04-08

## Motivacion
Elevar la UI del formulario hacia una direccion moderna, elegante y de alta gama usando como referencia el repositorio `nextlevelbuilder/ui-ux-pro-max-skill`.

## Estado actual
Existe una UI funcional, pero con lenguaje visual SaaS generalista y menor diferenciacion premium.

## Comportamiento deseado
Aplicar una direccion visual editorial-premium con mejor jerarquia tipografica, paleta marfil/carbon/oro y una composicion mas sofisticada.

## Alcance e impacto

### Area funcional afectada
- Presentacion visual del flujo de intake

### Area tecnica afectada
- Archivos: `product/intake-form/src/*`, `product/intake-form/tailwind.config.js`
- Documentacion: `docs/diseno/*`, `CHANGELOG.md`

### Impacto visual (si aplica)
- Componentes afectados: `Button`, `Field`, `Stepper`, layout principal del formulario
- ¿Rompe o extiende el design system?: Extiende el design system existente y redefine foundations visuales

## Supuestos
- La prioridad es sofisticacion visual sin cambiar el flujo funcional del PRD.
- Se mantiene accesibilidad base y performance razonable.

## Riesgos
- Un uso excesivo de glass/transparencia podria dañar contraste; se mitiga con capas suaves y fondos claros.

## Decisiones relacionadas
- Complementa ADR: [0004] Stack React + Vite + Tailwind para feature intake-form
- Relacionado con: `docs/diseno/decisiones/premium-editorial-direction.md`

## Estado de implementacion
Implementado

## Verificacion realizada
- [x] Lint ejecutado
- [x] Build ejecutado
- [x] Foundations de diseño actualizadas

## Follow-ups
- Validar visualmente con screenshots o pruebas E2E si el flujo sigue siendo consistente en mobile.
