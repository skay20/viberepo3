# Guía de QA y Verificación

Instrucciones para asegurar que cada cambio importante se verifique antes de darse por terminado.

---

## Filosofía
La prioridad no es inventar burocracia sino reducir roturas reales.
No todo necesita una suite de tests completa, pero todo cambio relevante necesita verificación honesta.

## Niveles de verificación

### Cambio menor (fix cosmético, typo, ajuste de config)
- Confirmar que el proyecto sigue compilando/corriendo
- Revisar que no se rompió nada visible

### Cambio moderado (nueva feature, refactor de módulo)
- Ejecutar checklist completo (ver [checklist.md](checklist.md))
- Verificar impacto lateral en módulos relacionados
- Actualizar docs si cambia comportamiento

### Cambio grande (nueva capa, migración, cambio de arquitectura)
- Todo lo anterior
- Crear decisión en docs/decisiones/
- Revisar coherencia con PRD y decisiones previas
- Documentar qué se verificó y qué no se pudo verificar
- Identificar riesgos residuales

## Qué significa "esto está listo"
Un cambio está listo cuando:
1. El código compila sin errores
2. Los tests existentes pasan (si hay tests)
3. Se verificó el comportamiento nuevo
4. Se documentó el cambio en `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado)
5. Se creó una decisión si fue una elección no trivial
6. El proyecto puede ejecutarse después del cambio
7. Se declaró explícitamente qué se verificó y qué no

## Qué hacer cuando algo no se puede verificar completamente
- Documentar qué queda sin verificar y por qué
- Registrar como riesgo conocido en docs/run/README.md
- No cerrar la tarea como si estuviera 100% completa si no lo está
- Sugerir cómo verificarlo después

## Anti-patrones de QA
- "Funciona en mi máquina" sin explicar el entorno
- Cerrar tareas sin haber corrido el proyecto
- Asumir que un cambio no tiene impacto lateral
- Inventar tests que no prueban nada real
- Reportar "todo OK" sin especificar qué se revisó
