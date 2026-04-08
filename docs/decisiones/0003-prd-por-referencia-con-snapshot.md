# [0003] PRD por referencia con snapshot versionado

## Estado
Aceptada

## Fecha
2026-04-08

## Contexto
El flujo anterior pedía pegar el PRD completo en `PRD.md`, lo que agregaba fricción operativa y pérdida de tiempo al iniciar proyectos.
Además, era necesario alinear un comportamiento único para Codex y Claude sin introducir automatizaciones pesadas.

## Opciones consideradas

### Opción A: Mantener copy/paste manual en `PRD.md`
- Ventajas: simple de entender.
- Desventajas: fricción alta, mayor riesgo de desactualización y duplicación manual.

### Opción B: Referencia explícita de PRD + snapshot en repo
- Ventajas: menos fricción, trazabilidad persistente, operación alineada Codex/Claude.
- Desventajas: requiere disciplina de ingesta y actualización de manifiesto.

### Opción C: Referencia externa sin snapshot local
- Ventajas: mínimo almacenamiento.
- Desventajas: menor reproducibilidad y trazabilidad en el tiempo.

## Decisión
Adoptar **Opción B**:
- referencia explícita del PRD en prompt (ruta, adjunto o URL),
- ingesta documentada con snapshot versionado en `docs/contexto/prd-fuentes/`,
- `PRD.md` pasa a ser manifiesto operativo (fuente activa, última ingesta, snapshot y tier).

## Consecuencias
- Se elimina la necesidad de copy/paste manual como flujo principal.
- Se mejora la consistencia entre Codex y Claude mediante contrato común (`docs/operacion/fuente-prd.md`).
- `PRD-template.md` queda como alternativa opcional.
- Supuesto adoptado: al inicio de proyecto/tarea grande, el usuario siempre indica referencia del PRD.
- Follow-up: en repos hijos, aplicar el mismo contrato y convención de snapshots.

## Área afectada
Arquitectura | Producto | QA

## Relación con otras decisiones
- Complementa: [0001] y [0002]
- Reemplaza: ninguna
