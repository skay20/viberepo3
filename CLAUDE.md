# CLAUDE.md — Instrucciones Operativas para Claude

Este archivo es la memoria viva del proyecto para Claude.
Léelo completo al inicio de cada sesión antes de ejecutar cualquier tarea.

---

## Detección de modo

Antes de actuar, detectar modo con `git remote get-url origin`:

- Si `origin` es `https://github.com/skay20/VibeRepo.git` o `git@github.com:skay20/VibeRepo.git` => **repo base (framework)**.
- En cualquier otro caso => **repo derivado (proyecto activo)**.
- Si no hay `origin`, asumir repo derivado y declarar ese supuesto.

### Reglas por modo

- **Repo base**: solo cambios de gobernanza/documentación del framework. No ejecutar PRDs, no crear snapshots en `docs/contexto/prd-fuentes/`, no implementar en `product/`, y registrar cambios en `FRAMEWORK_CHANGELOG.md`.
- **Repo derivado**: aplicar flujo normal completo de PRD, snapshots, ejecución y documentación viva. Registrar cambios en `CHANGELOG.md`.
- Si el cambio toca gobernanza, contratos, QA o arquitectura del framework base, invocar la especialidad `framework-sanitizer` antes de cerrar.

## Propósito del repo

Este es un repositorio base clonable para iniciar proyectos desde un PRD.
Contiene gobernanza, memoria de decisiones, documentación viva y soporte para Codex y Claude.
No es un framework de agentes. Es una base de trabajo gobernada por instrucciones y documentación.

## Antes de actuar

Lee estos archivos en orden antes de cualquier modificación:

1. Detectar modo (base/derivado) con la regla anterior.
2. **docs/operacion/estado-sesion.md** — Estado actual del proyecto. Orientación rápida de dónde estamos.
3. **docs/operacion/fuente-prd.md** — Contrato para resolver fuente PRD desde el prompt (**solo repo derivado**).
4. **PRD.md** — Manifiesto operativo (fuente activa, snapshot, tier) (**solo repo derivado**).
5. **docs/contexto/prd-fuentes/(snapshot activo)** — PRD fundacional completo (**solo repo derivado**).
6. **docs/contexto/README.md** — Stack, entorno, integraciones, restricciones.
7. **docs/decisiones/README.md** — Índice de decisiones. Revisar todas las existentes.
8. **docs/cambios/README.md** — Cambios post-PRD registrados.
9. **FRAMEWORK_CHANGELOG.md** (**repo base**) o **CHANGELOG.md** (**repo derivado**).
10. **docs/diseno/README.md** — Design system y gobernanza visual (si hay UI).
11. **docs/run/README.md** — Cómo se ejecuta el proyecto.
12. **docs/operacion/contrato-ejecucion.md** — Contrato anti-skip y formato de cierre.

Si el PRD activo (snapshot) es extenso, procesarlo por secciones: primero visión y alcance, luego requisitos, luego detalles técnicos. No perder contexto general al trabajar en partes específicas.

## Tiers de ejecución

El tier define cuánto proceso aplicar. Se declara en PRD.md al inicio del proyecto o de la tarea.
Si no está definido, asumir `standard`.

| Tier | Cuándo aplica | Qué requiere |
|------|---------------|--------------|
| `lean` | Copy, estilos, typos, refactor local sin impacto funcional | Entry en changelog según modo + compilar (si aplica) |
| `standard` | Nueva feature, cambio de lógica, nueva ruta, UI nueva | ADR si hay decisión + QA checklist + closure tag |
| `strict` | Auth, DB schema, deps críticas, cambios arquitectónicos, seguridad | Todo lo anterior + impacto en decisiones existentes documentado + `docs/operacion/gate-release.md` |

## Contrato de fuente PRD (obligatorio)

- Aplicar `docs/operacion/fuente-prd.md` como contrato común con AGENTS.md.
- Aplica solo en repo derivado. En repo base no se ejecuta ingesta PRD.
- En inicio de proyecto o tarea grande, exigir referencia explícita del PRD en el prompt.
- Si falta referencia en ese contexto, no ejecutar implementación y solicitar fuente.
- Con referencia válida, generar snapshot en `docs/contexto/prd-fuentes/` y actualizar `PRD.md`.
- Evitar pedir copy/paste manual del PRD salvo bloqueo real de acceso.

## Reglas de trabajo

### Contexto primero
- No actúes sin haber leído el PRD y las decisiones previas.
- No improvises arquitectura si ya hay una documentada en `docs/arquitectura/README.md`.
- No asumas stack ni tecnologías si no están definidos. Pregunta.

### Preguntar ante vacíos
- Si falta información crítica (stack, restricciones, integraciones, seguridad, diseño), pregunta antes de asumir.
- Si una duda no bloquea, márcala como supuesto o decisión pendiente en el ADR correspondiente.
- Detecta ambigüedades en el PRD y señálalas antes de implementar.

### Running-first
- Todo cambio debe dejar el proyecto en estado ejecutable.
- Si algo queda parcial, documentar qué falta en `docs/run/README.md`.
- Nunca des por terminada una tarea si el proyecto no compila sin explicarlo.

### Contrato anti-skip (obligatorio)
- Aplicar `docs/operacion/contrato-ejecucion.md` como contrato común con AGENTS.md.
- Cerrar siempre con etiqueta explícita: `ENTREGA COMPLETA` o `ENTREGA PARCIAL`.
- En tareas grandes o si el pedido es "ejecutar todo el PRD", incluir Matriz de cobertura PRD.
- Prohibido afirmar "terminado" si quedan secciones del PRD pendientes dentro del alcance solicitado.
- Si la entrega es parcial, incluir plan por fases (`completado / en progreso / pendiente`), bloqueos y siguiente acción.
- Si hay riesgo alto o cambio grande, pedir aprobación explícita antes de continuar.

### No duplicar
- Antes de crear algo nuevo, verificar que no exista ya.
- Buscar funciones, componentes, utilidades y patrones existentes.
- Reutilizar antes de crear. Extender antes de duplicar.

## Anti-hallucination

1. No inventes APIs, endpoints, funciones o tipos que no existan en el codebase.
2. No asumas que un archivo existe sin verificarlo primero con Glob o Read.
3. No importes paquetes que no estén instalados.
4. No afirmes que algo funciona sin haberlo verificado.
5. No generes datos de ejemplo como si fueran reales.
6. No hardcodees valores configurables.

## Decisiones

Cuando tomes una decisión no trivial:

1. Crear un ADR en `docs/decisiones/` usando `_template-adr.md`.
2. Numerar secuencialmente (siguiente número disponible).
3. Registrar contexto, opciones consideradas, decisión tomada y consecuencias.
4. Actualizar el índice en `docs/decisiones/README.md`.

Las decisiones son append-only. Para cambiar una decisión previa, crear una nueva que la reemplace y marcar la anterior como "Reemplazada por NNNN".

Nunca contradigas una decisión previa sin dejar rastro.

## Cambios post-PRD

El PRD fundacional es inmutable una vez que el proyecto arranca.
Los cambios posteriores se registran en `docs/cambios/`:

1. Usar `_template-cambio.md` para cada cambio relevante.
2. Vincular cada cambio a: motivo, área afectada, impacto y decisiones relacionadas.
3. Si un cambio contradice el PRD o una decisión previa, requiere un ADR nuevo.
4. Actualizar el índice en `docs/cambios/README.md`.

## Criterio de cambio grande y riesgo alto

Un cambio es grande si cumple al menos uno:
- Afecta más de 3 archivos en áreas diferentes
- Cambia la arquitectura o estructura del proyecto
- Modifica el modelo de datos
- Introduce o remueve una dependencia importante
- Cambia el comportamiento de un flujo principal
- Contradice una decisión previa

Riesgo alto: seguridad, datos, cumplimiento, migraciones irreversibles, impacto operacional severo o incertidumbre sin rollback claro.

## Gobernanza de diseño

> Solo aplica si el proyecto tiene frontend o capa visual relevante.

### Reglas base
- Revisar `docs/diseno/README.md` antes de crear cualquier componente visual.
- Si existe un `DESIGN.md` aplicable al scope actual, leerlo antes de diseñar o implementar UI. Para `product/intake-form`, la referencia activa es `product/intake-form/DESIGN.md`.
- `DESIGN.md` define dirección visual; `CLAUDE.md` define proceso, calidad y ejecución.
- Si la referencia visual entra en conflicto con el producto real, priorizar usabilidad, accesibilidad y coherencia del dominio antes que la imitación estilística.
- Reutilizar componentes existentes. Si no hay uno adecuado, documentar el nuevo en `docs/diseno/componentes/`.
- No hardcodear colores, spacing, tipografía o sombras. Usar tokens o variables.
- Si un patrón visual aparece más de dos veces, evaluar para promoción a componente compartido.
- Documentar excepciones visuales en `docs/diseno/decisiones/`.
- Revisar accesibilidad básica: labels, contraste, navegación por teclado.

### Regla de cierre para UI nueva (obligatoria)

**Trigger:** la tarea crea la primera UI real del proyecto, O introduce un patrón visual nuevo relevante.

**Mínimo obligatorio antes de `ENTREGA COMPLETA`:**
- Foundations definidas en `docs/diseno/README.md`: color, tipografía, spacing, radius, border/shadow, states
- Tokens implementados en código (sin valores visuales hardcodeados)
- Componentes base extraídos si ya hay repetición real en la UI
- Componentes base documentados en `docs/diseno/componentes/`

**Regla de cierre dura:**
Si hay UI nueva Y `docs/diseno/README.md` sigue con foundations vacías, o las decisiones visuales relevantes quedaron solo en código sin documentar → **no se puede declarar `ENTREGA COMPLETA`.**

**Anti-sobreingeniería:**
No crear un design system completo por defecto. Solo materializar la capa mínima que la UI actual ya justifica. No abstraer componentes que todavía no sean patrón real.

## QA y verificación

Antes de cerrar cualquier cambio importante:

1. Revisar `docs/qa/checklist.md` y aplicar los items relevantes.
2. Verificar que el proyecto compila y corre.
3. Correr tests existentes si los hay.
4. Declarar explícitamente qué verificaste y qué no pudiste verificar.
5. Si algo quedó sin verificar, documentar en `docs/run/README.md` como riesgo conocido.
6. Cumplir el formato de cierre del contrato (`ENTREGA COMPLETA/PARCIAL` + matriz PRD cuando aplique).
7. Para tier `strict` o antes de merge a main: completar `docs/operacion/gate-release.md`.

## Changelog

Actualizar `FRAMEWORK_CHANGELOG.md` (repo base) o `CHANGELOG.md` (repo derivado) con cada cambio relevante:
- Qué cambió
- Por qué cambió
- Impacto y áreas afectadas
- Follow-ups pendientes

No es un dump de commits. Es trazabilidad útil para humanos.

## Definition of Done

Una tarea está terminada cuando:
- [ ] Cumple el requisito del PRD o change request
- [ ] El proyecto compila y corre
- [ ] Tests existentes pasan
- [ ] Se creó ADR si hubo decisión no trivial
- [ ] Se actualizó `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado)
- [ ] Se actualizó documentación afectada
- [ ] Se resolvió fuente PRD y se actualizó `PRD.md` (solo derivado, si fue inicio de proyecto o tarea grande)
- [ ] Se etiquetó el cierre como `ENTREGA COMPLETA` o `ENTREGA PARCIAL`
- [ ] Se incluyó Matriz de cobertura PRD (si fue tarea grande o PRD completo)
- [ ] Si fue `ENTREGA PARCIAL`, se documentaron fases, bloqueos y siguiente acción
- [ ] Se declaró qué se verificó y qué no (verificado/no verificado)
- [ ] El design system se respetó (si aplica)
- [ ] El repo quedó igual o más ordenado que antes

## Estructura del repo

```
PRD.md                             — Manifiesto operativo del PRD activo
PRD-template.md                    — Plantilla opcional de PRD completo
FRAMEWORK_CHANGELOG.md             — Registro de cambios del repo base
CHANGELOG.md                       — Registro de cambios del repo derivado
AGENTS.md                          — Instrucciones para Codex
CLAUDE.md                          — Este archivo
.claude/settings.json              — Permisos operativos de Claude (allow/deny)
.claude/agents/                    — Wrappers de agentes Claude para el repo base

docs/contexto/                     — Stack, entorno, integraciones, restricciones
docs/contexto/prd-fuentes/         — Snapshots versionados de PRDs referenciados
docs/decisiones/                   — ADRs y memoria de decisiones
docs/cambios/                      — Change requests post-PRD
docs/arquitectura/                 — Guía de arquitectura y buenas prácticas
docs/qa/                           — QA y checklists de verificación
docs/diseno/                       — Design system y gobernanza visual (si hay UI)
docs/run/                          — Estado ejecutable, setup, errores conocidos
docs/operacion/
  fuente-prd.md                    — Contrato de referencia e ingesta PRD
  contrato-ejecucion.md            — Contrato anti-skip + Matriz PRD
  gate-release.md                  — Checklist pre-merge/release por tier
  estado-sesion.md                 — Snapshot del proyecto (leer primero en cada sesión)
docs/especialidades/               — Estructura para subagentes futuros
product/README.md                  — Setup operativo del producto derivado
skills/framework-sanitizer/        — Skill Codex para sanear drift documental del framework base
```

## Diferencias con AGENTS.md

Ambos archivos comparten la misma gobernanza base. Las diferencias son de formato:
- AGENTS.md usa protocolos numerados paso a paso (optimizado para Codex).
- CLAUDE.md usa secciones temáticas con reglas claras (optimizado para Claude).
- Las reglas, rutas y principios son los mismos.
