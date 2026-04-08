# [0002] Convención de carpeta product/ para implementación de producto

## Estado
Aceptada

## Fecha
2026-04-07

## Contexto
Al usar VibeRepo como base clonable, la raíz del repo contiene gobernanza y documentación del framework (AGENTS.md, CLAUDE.md, docs/, plantillas). Mezclar código de producto en la raíz junto con archivos de gobernanza genera ambigüedad: no queda claro qué pertenece al template y qué pertenece al proyecto específico.

## Opciones consideradas

### Opción A: Código de producto en raíz (app/, src/, components/, etc.)
- Ventajas: estructura familiar en proyectos nuevos, sin carpeta extra
- Desventajas: mezcla framework con implementación, dificulta actualizar la gobernanza sin tocar el producto, confunde al modelo sobre qué archivos son del template y cuáles del proyecto

### Opción B: Código de producto en product/
- Ventajas: separación clara entre gobernanza (raíz) e implementación (product/), fácil de identificar qué es framework y qué es proyecto, facilita updates al template
- Desventajas: un nivel extra de carpeta, puede requerir ajustes en configs de build/deploy

### Opción C: Estructura libre con excepción documentada
- Ventajas: flexibilidad total
- Desventajas: inconsistencia entre proyectos derivados

## Decisión
Se adopta `product/` como convención por defecto para todo código nuevo de producto.
La raíz se reserva para gobernanza del framework: instrucciones de modelos, documentación, plantillas y configuración compartida.

Las excepciones están permitidas (ej: `apps/<slug>` en monorepos) pero deben documentarse con un ADR o change request.

Los proyectos que ya tienen código en raíz (legado) pueden mantenerlo así — esta política aplica a nuevas implementaciones.

## Consecuencias
- Todo proyecto derivado de VibeRepo debe crear `product/` al iniciar la implementación
- Los comandos de build/run se ejecutan desde `product/` (ver docs/run/README.md)
- Si se detecta código de producto en raíz sin excepción documentada, es un gap a corregir
- La separación facilita actualizar el template de gobernanza sin afectar el código del producto

## Área afectada
Arquitectura | Producto

## Relación con otras decisiones
- Complementa: [0001] Adoptar VibeRepo como base de proyecto
