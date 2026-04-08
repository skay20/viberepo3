# Guía de Arquitectura

Principios y reglas para mantener la arquitectura del proyecto limpia, coherente y mantenible.

---

## Principios fundamentales

### 1. Estructura clara
- Cada carpeta y archivo debe tener un propósito evidente
- Si un archivo crece demasiado, dividirlo por responsabilidad
- Nombrar archivos y carpetas de forma descriptiva y consistente

### 2. Separación de responsabilidades
- Cada módulo, componente o servicio hace una sola cosa bien
- No mezclar lógica de negocio con lógica de presentación
- No mezclar acceso a datos con transformaciones de datos
- Las capas se comunican a través de interfaces claras

### 3. Bajo acoplamiento
- Los módulos deben poder cambiar internamente sin romper otros
- Preferir composición sobre herencia
- Evitar dependencias circulares
- Inyectar dependencias cuando sea razonable, no cuando sea ceremonial

### 4. Convenciones de nombres
- Usar un patrón consistente en todo el proyecto (camelCase, snake_case, kebab-case)
- Definir la convención al inicio y documentarla aquí
- No mezclar convenciones sin razón

### 5. Escalabilidad razonable
- Diseñar para lo que se necesita hoy más un margen sensato
- No sobrearquitectar para escenarios hipotéticos
- No subarquitectar si el crecimiento es previsible
- Preferir la solución más simple que resuelva el problema real

### 6. Mantenibilidad
- Código que se entienda sin documentación excesiva
- Funciones cortas con nombres claros
- Evitar abstracciones prematuras: si algo se usa una sola vez, no necesita ser genérico
- Si un patrón se repite tres veces, evaluar abstracción

## Anti-patrones a evitar
- Enterprise theater: capas, factories o abstracciones sin justificación
- God files: archivos con múltiples responsabilidades mezcladas
- Copy-paste driven development: duplicar en lugar de reutilizar
- Magic strings/numbers: valores hardcodeados sin contexto
- Dependencias innecesarias: no agregar una librería para algo trivial

## Política de estructura de carpetas (framework vs producto)

### Regla base
- La raíz del repo se reserva para framework y gobernanza (`AGENTS.md`, `CLAUDE.md`, `docs/`, plantillas y configuración compartida).
- La implementación nueva de producto debe vivir por defecto en `product/`.

### Prohibición
- No crear código nuevo de producto en raíz (`app/`, `src/`, `components/`, `lib/`, etc.) salvo excepción documentada.

### Excepciones permitidas
- Si se usa una estructura distinta (por ejemplo `apps/<slug>`), debe justificarse explícitamente en:
  - un ADR en `docs/decisiones/`, o
  - una nota de cambio en `docs/cambios/`.

### Nota de migración para repos existentes
- Si ya existe implementación en raíz, se considera legado permitido.
- A partir de esta política, nuevas features deberían ir en `product/` o dejar excepción documentada.

## Convenciones del proyecto
(completar cuando se defina el stack)

- Lenguaje principal: 
- Convención de nombres: 
- Estructura de carpetas: 
- Patrones de diseño adoptados: 
- Patrones explícitamente descartados: 

## Diagrama de arquitectura
(agregar cuando exista - puede ser ASCII, Mermaid o referencia a imagen)
