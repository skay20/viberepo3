# [CR-0004] Adaptar DESIGN.md como nueva direccion visual del intake

## Tipo
Change Request

## Fecha
2026-04-10

## Motivación
Existe una guía visual importada en `product/intake-form/DESIGN.md` inspirada en ElevenLabs.
Se necesita usarla como referencia real para una mejora visible del producto, evitando copia literal y descartando patrones de audio o marketing que no correspondan al dominio.

## Estado actual
La app ya contaba con un refresh premium/editorial y una base parcial de `shadcn/ui`.
El sistema era funcional y consistente, pero más cálido y editorial que técnico.

## Comportamiento deseado
La UI debe adoptar una presencia más moderna, de alta gama y limpia:
- shell principal más refinado
- navegación mínima más clara
- botones, inputs y cards mejor alineados
- contraste alto y superficies elegantes
- documentación operativa actualizada para exigir lectura de `DESIGN.md` en trabajos de UI

## Alcance e impacto

### Área funcional afectada
- Shell principal de `product/intake-form`
- Intro, formulario multi-step y estado final

### Área técnica afectada
- Archivos: `product/intake-form/src/*`, `AGENTS.md`, `CLAUDE.md`, `docs/diseno/*`, `docs/decisiones/*`, `CHANGELOG.md`
- Módulos: design tokens, primitives UI, shell del formulario

### Impacto visual (si aplica)
- Componentes afectados: `Button`, `Field`, `Stepper`, `Card`, layout principal
- ¿Rompe o extiende el design system?: extiende y reemplaza la fuente de referencia visual activa

## Supuestos
- La referencia `DESIGN.md` debe interpretarse como dirección abstracta.
- No se añaden dependencias nuevas para esta pasada.

## Riesgos
- Un cambio demasiado aspiracional podría degradar legibilidad si no se controla contraste.
- Cambiar la dirección visual sin documentarla produciría drift entre código y gobernanza.

## Decisiones relacionadas
- Complementa ADR: [0005]
- Complementa ADR: [0006]

## Estado de implementación
Implementado

## Verificación realizada
- [x] `npm run lint`
- [x] `npm run build`

## Follow-ups
- Validar visualmente el shell en móvil real y desktop ancho.
- Si crece el producto, extender la dirección a futuras pantallas usando la misma referencia.
