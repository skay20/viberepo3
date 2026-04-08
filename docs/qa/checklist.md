# Checklist de Verificación Pre-Entrega

Usar este checklist antes de considerar terminado un cambio importante.
No todos los items aplican a todos los cambios. Marcar N/A cuando no corresponda.

---

## Compilación y ejecución
- [ ] El proyecto compila sin errores
- [ ] El proyecto se ejecuta correctamente después del cambio
- [ ] No hay errores nuevos en consola o logs

## Tests
- [ ] Los tests existentes pasan
- [ ] Se agregaron tests para el comportamiento nuevo (si aplica)
- [ ] No se deshabilitaron tests existentes sin justificación

## Código
- [ ] No se hardcodearon secretos, credenciales o API keys
- [ ] No se importaron paquetes no instalados
- [ ] No se crearon archivos fuera del plan o la estructura esperada
- [ ] No se duplicó lógica que ya existía
- [ ] Se respetaron las convenciones de nombres del proyecto
- [ ] No se introdujeron dependencias innecesarias

## Arquitectura
- [ ] El cambio es coherente con la arquitectura documentada
- [ ] No se mezclan responsabilidades sin justificación
- [ ] Si se cambió la arquitectura, se creó un ADR en docs/decisiones/

## Diseño y UI (si aplica)
- [ ] Se revisó el design system antes de crear componentes nuevos
- [ ] Se reutilizaron componentes existentes donde fue posible
- [ ] No se hardcodearon valores visuales que deberían ser tokens
- [ ] La UI es consistente con el resto del proyecto
- [ ] Se consideró accesibilidad básica (labels, contraste, teclado)
- [ ] Si fue primera UI o patrón visual nuevo: foundations definidas en `docs/diseno/README.md` (ver regla de cierre)
- [ ] Si fue primera UI o patrón visual nuevo: componentes base documentados en `docs/diseno/componentes/`
- [ ] Si foundations o componentes siguen vacíos con UI nueva → declarar `ENTREGA PARCIAL`, no `COMPLETA`

## Documentación
- [ ] Se actualizó `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado)
- [ ] Se creó decisión en docs/decisiones/ si fue necesario
- [ ] Se actualizó docs/contexto/README.md si cambió el stack o entorno
- [ ] Se actualizó docs/run/README.md si cambiaron los pasos de ejecución

## Gobernanza anti-skip
- [ ] Si fue inicio de proyecto o tarea grande, se resolvió fuente PRD según `docs/operacion/fuente-prd.md`
- [ ] Si se ingirió PRD, existe snapshot en `docs/contexto/prd-fuentes/` y `PRD.md` actualizado
- [ ] Se declaró `ENTREGA COMPLETA` o `ENTREGA PARCIAL`
- [ ] Se incluyó Matriz de cobertura PRD si fue tarea grande o PRD completo (formato en `docs/operacion/contrato-ejecucion.md`)
- [ ] Se siguió la política de carpetas (`product/`) o se documentó excepción en `docs/decisiones/`
- [ ] Si fue `ENTREGA PARCIAL`, se documentaron fases pendientes y bloqueos
- [ ] Para tier `strict` o merge a main: se completó `docs/operacion/gate-release.md`

## Verificación declarada
- [ ] Se documentó qué se verificó
- [ ] Se documentó qué NO se pudo verificar (si algo quedó pendiente)
