# [0006] Adoptar DESIGN.md como direccion visual activa para intake form

## Estado
Aceptada

## Fecha
2026-04-10

## Contexto
El producto `product/intake-form` ya tenia una direccion visual premium/editorial y una base inicial de `shadcn/ui`.
Luego se importó `product/intake-form/DESIGN.md` usando `getdesign` con referencia a ElevenLabs.

El cambio no afecta arquitectura ni lógica de negocio, pero sí redefine la fuente primaria de inspiración visual y contradice parcialmente la dirección más cálida y editorial adoptada antes.

## Opciones consideradas

### Opción A: Mantener la dirección editorial previa
- Ventajas: menos trabajo, continuidad total con el estado visual existente
- Desventajas: desaprovecha la nueva referencia visual y mantiene una estética menos técnica para el producto actual

### Opción B: Copiar ElevenLabs de forma literal
- Ventajas: rapidez aparente y resultado reconocible
- Desventajas: riesgo de incoherencia con el dominio, problemas de identidad y mala traducción de patrones de audio a recruiting

### Opción C: Usar DESIGN.md como guía abstracta y adaptada
- Ventajas: incorpora una dirección visual más moderna y sobria sin copiar marca ni patrones de dominio ajenos
- Desventajas: exige criterio para traducir qué conservar y qué descartar

## Decisión
Se adopta la opción C.

`product/intake-form/DESIGN.md` pasa a ser la referencia visual activa para el producto, interpretada de forma abstracta. Se retienen principios de contraste, tipografía, superficies y CTAs refinados, pero se descartan patrones específicos de audio o marketing que no correspondan al flujo de intake.

## Consecuencias
- El shell visual cambia hacia chrome oscuro con paneles claros y acento cálido controlado.
- `AGENTS.md` y `CLAUDE.md` deben exigir lectura de `DESIGN.md` antes de tareas de UI cuando exista una guía aplicable.
- Se prioriza usabilidad, accesibilidad y coherencia del producto por encima de la fidelidad estética a la referencia.
- La decisión visual previa queda superada como fuente principal de inspiración, pero no invalida la base reusable ya construida.

## Área afectada
Diseño

## Relación con otras decisiones
- Complementa: [0005]
- Reemplaza: ninguna ADR técnica; sustituye la referencia visual anterior como fuente activa
