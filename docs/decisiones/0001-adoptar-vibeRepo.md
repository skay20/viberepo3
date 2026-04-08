# [0001] Adoptar VibeRepo como base de proyecto

## Estado
Aceptada

## Fecha
2026-04-06

## Contexto
Se necesita una base reusable para iniciar proyectos desde un PRD, con soporte para Codex y Claude, gobernanza simple, memoria de decisiones y documentación viva.

## Opciones consideradas

### Opción A: Repo vacío con README mínimo
- Ventajas: cero overhead inicial
- Desventajas: cada proyecto empieza sin estructura, se pierde contexto, se repiten errores

### Opción B: VibeRepo como plantilla gobernada
- Ventajas: estructura consistente, memoria persistente, gobernanza desde el día uno, soporte multi-LLM
- Desventajas: requiere inversión inicial en documentación

## Decisión
Se adopta VibeRepo como plantilla base. Cada nuevo proyecto se inicia clonando este repo, completando PRD.md y siguiendo la gobernanza definida en AGENTS.md y CLAUDE.md.

## Consecuencias
- Todo proyecto nuevo arranca con estructura de decisiones, cambios, QA y diseño
- Los modelos (Codex/Claude) tienen instrucciones operativas desde el primer momento
- La documentación se mantiene viva, no se crea una vez y se abandona
- Las especialidades se definen según necesidad real, no por anticipación

## Área afectada
Arquitectura | Producto

## Relación con otras decisiones
- Primera decisión del repo. Fundacional.
