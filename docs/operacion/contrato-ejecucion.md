# Contrato de Ejecucion (No-Skip)

Contrato operativo comun para Codex y Claude.
Este documento define como cerrar tareas grandes sin entregas parciales silenciosas.

---

## Objetivo

- Evitar cierres ambiguos o incompletos cuando se pide ejecutar un PRD completo.
- Estandarizar el formato de cierre y la trazabilidad de cobertura del PRD.
- Forzar transparencia de verificacion y bloqueos.

## Alcance

Aplica a cualquier tarea de implementacion, y es obligatorio para:

- "Ejecutar todo el PRD"
- Cambios grandes
- Entregas multi-fase o con dependencias externas

## Definiciones

### ENTREGA COMPLETA
La tarea solicitada esta implementada en su alcance acordado y no quedan secciones del PRD en estado pendiente dentro de ese alcance.

### ENTREGA PARCIAL
La tarea no pudo completarse en un turno o quedo bloqueada por riesgos, dependencias o decisiones pendientes.

### Cambio grande
Se considera cambio grande si cumple al menos uno:

- Afecta mas de 3 archivos en areas diferentes
- Cambia la arquitectura o estructura del proyecto
- Modifica el modelo de datos
- Introduce o remueve una dependencia importante
- Cambia el comportamiento de un flujo principal
- Contradice una decision previa

### Riesgo alto
Situacion con probabilidad alta de impacto severo, por ejemplo:

- Riesgo de seguridad, privacidad o cumplimiento regulatorio
- Perdida/corrupcion de datos o migraciones irreversibles
- Interrupcion de flujo principal o downtime relevante
- Costos de infraestructura/terceros fuera de umbral esperado
- Cambio con alta incertidumbre tecnica sin rollback claro

## Reglas Obligatorias (No-Skip)

1. Si el usuario pide "ejecutar todo el PRD", no se permite cerrar sin declarar cobertura real.
2. Prohibido afirmar "terminado" si hay secciones del PRD pendientes dentro del alcance solicitado.
3. Si no se puede completar todo en un turno, se debe cerrar como `ENTREGA PARCIAL`.
4. En `ENTREGA PARCIAL`, incluir plan por fases con estado:
   `completado / en progreso / pendiente`.
5. En `ENTREGA PARCIAL`, incluir bloqueos y proximo paso recomendado.
6. Si hay riesgo alto o cambio grande, pedir aprobacion explicita antes de continuar.
7. Toda entrega debe declarar que se verifico y que no se pudo verificar.

## Matriz De Cobertura PRD (Obligatoria)

Incluir esta matriz en cierre de tareas grandes o cuando se solicite ejecutar el PRD completo:

| Seccion PRD | Estado | Evidencia (archivo/ruta) | Bloqueos |
|-------------|--------|--------------------------|----------|
| ... | Completado / En progreso / Pendiente / Bloqueado | ... | ... |

## Formato Minimo De Cierre

1. Etiqueta obligatoria: `ENTREGA COMPLETA` o `ENTREGA PARCIAL`.
2. Estado de verificacion:
- Verificado: ...
- No verificado: ...
3. Matriz de cobertura PRD (si aplica por alcance).
4. Si es parcial:
- Plan por fases
- Bloqueos
- Siguiente accion recomendada

## Relacion Con Otros Documentos

- `AGENTS.md` y `CLAUDE.md` deben referenciar este contrato y no contradecirlo.
- `docs/operacion/fuente-prd.md` define como se resuelve e ingiere el PRD activo.
- `docs/qa/checklist.md` valida su cumplimiento.
- `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado) debe registrar cambios relevantes de esta gobernanza.
