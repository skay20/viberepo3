# AGENTS.md — Instrucciones Operativas para Codex

Este archivo gobierna el comportamiento de Codex al trabajar en este repositorio.
Léelo completo antes de ejecutar cualquier tarea.

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

## Protocolo: Antes de actuar

Antes de escribir código o modificar archivos, ejecuta estos pasos en orden:

1. Detectar modo (base/derivado) con la regla anterior.
2. Leer `docs/operacion/estado-sesion.md` — snapshot del estado actual del proyecto.
3. Resolver la fuente del PRD desde el prompt siguiendo `docs/operacion/fuente-prd.md` (**solo repo derivado**).
4. Leer `PRD.md` como manifiesto operativo (fuente activa, snapshot, tier) (**solo repo derivado**).
5. Leer el snapshot activo en `docs/contexto/prd-fuentes/` (**solo repo derivado**).
6. Leer `docs/contexto/README.md` para entender stack, entorno e integraciones.
7. Leer `docs/decisiones/README.md` y revisar las decisiones existentes.
8. Leer `docs/cambios/README.md` para ver si hay cambios posteriores al PRD.
9. Leer `FRAMEWORK_CHANGELOG.md` (**repo base**) o `CHANGELOG.md` (**repo derivado**).
10. Si hay UI, leer `docs/diseno/README.md` para conocer el design system.
11. Revisar `docs/run/README.md` para saber cómo se ejecuta el proyecto.
12. Revisar `docs/operacion/contrato-ejecucion.md` para cumplir el contrato anti-skip.

No actuar sin contexto. Si algo no está claro, preguntar.

## Tiers de ejecución

El tier define cuánto proceso aplicar. Se declara en PRD.md al inicio del proyecto o de la tarea.
Si no está definido, asumir `standard`.

| Tier | Cuándo aplica | Qué requiere |
|------|---------------|--------------|
| `lean` | Copy, estilos, typos, refactor local sin impacto funcional | Entry en changelog según modo + compilar (si aplica) |
| `standard` | Nueva feature, cambio de lógica, nueva ruta, UI nueva | ADR si hay decisión + QA checklist + closure tag |
| `strict` | Auth, DB schema, deps críticas, cambios arquitectónicos, seguridad | Todo lo anterior + impacto en decisiones existentes documentado + `docs/operacion/gate-release.md` |

## Protocolo: Fuente PRD (obligatorio)

Regla base: seguir `docs/operacion/fuente-prd.md` como contrato común con Claude.
Aplica solo en repo derivado. En repo base, no se ejecuta este protocolo.

1. Si el usuario inicia proyecto o tarea grande, exigir referencia explícita del PRD en el prompt.
2. Si falta referencia en ese contexto, no ejecutar implementación y pedir fuente.
3. Con referencia válida, crear snapshot en `docs/contexto/prd-fuentes/`.
4. Actualizar `PRD.md` con fuente activa, última ingesta y snapshot asociado.
5. Evitar pedir copy/paste manual del PRD salvo bloqueo real de acceso.

## Protocolo: Ejecutar cambios

1. Identificar el requisito a implementar (PRD/change request en derivado, o tarea de framework en base).
2. Verificar que no contradice una decisión existente en `docs/decisiones/`.
3. Detectar el stack real del proyecto antes de asumir convenciones técnicas.
4. Implementar el cambio respetando la arquitectura documentada en `docs/arquitectura/README.md`.
5. Si el cambio implica una decisión no trivial, crear un ADR en `docs/decisiones/` usando la plantilla.
6. Si el cambio es post-PRD, registrarlo en `docs/cambios/` usando la plantilla.
7. Actualizar `FRAMEWORK_CHANGELOG.md` (repo base) o `CHANGELOG.md` (repo derivado) con lo que cambió, por qué y su impacto.
8. Verificar que el proyecto compila y corre después del cambio.
9. Declarar explícitamente qué se verificó y qué no se pudo verificar.

## Protocolo: QA y verificación

Antes de considerar terminado un cambio:

1. Revisar `docs/qa/checklist.md` y aplicar los items relevantes.
2. Ejecutar el comando de build/compile si existe.
3. Ejecutar tests existentes si los hay.
4. Revisar impacto lateral en módulos relacionados.
5. Si algo no se pudo verificar, documentarlo explícitamente.
6. Aplicar el cierre obligatorio del contrato en `docs/operacion/contrato-ejecucion.md`.
7. Para tier `strict` o antes de merge a main: completar `docs/operacion/gate-release.md`.

Un cambio NO está terminado si:
- El proyecto no compila
- Los tests existentes fallan
- No se actualizó el changelog
- No se documentaron las decisiones relevantes

## Protocolo: Contrato de ejecución (anti-skip)

Regla base: seguir `docs/operacion/contrato-ejecucion.md` como fuente común con Claude.

1. Cerrar siempre con etiqueta explícita: `ENTREGA COMPLETA` o `ENTREGA PARCIAL`.
2. En tareas grandes o cuando el pedido sea "ejecutar todo el PRD", incluir Matriz de cobertura PRD.
3. Nunca declarar "terminado" si hay secciones del PRD pendientes dentro del alcance solicitado.
4. Si la entrega es parcial, incluir:
   - Plan por fases (`completado / en progreso / pendiente`)
   - Bloqueos
   - Siguiente acción recomendada
5. Si hay riesgo alto o cambio grande, pedir aprobación explícita antes de continuar.
6. Declarar explícitamente qué está verificado y qué no está verificado.

## Protocolo: Diseño y UI

> Solo aplica si el proyecto tiene frontend o capa visual.

1. Leer `docs/diseno/README.md` antes de crear cualquier componente nuevo.
2. Revisar componentes existentes en `docs/diseno/componentes/`.
3. Reutilizar antes de crear. Extender antes de duplicar.
4. Si se crea un componente nuevo, documentarlo en `docs/diseno/componentes/[nombre].md` usando `_template-componente.md`.
5. No hardcodear valores visuales que deban ser tokens o variables.
6. Si un cambio visual rompe o extiende una regla del design system, documentar la excepción en `docs/diseno/decisiones/`.

## Regla de cierre para UI nueva (obligatoria)

**Trigger:** la tarea crea la primera UI real del proyecto, O introduce un patrón visual nuevo relevante.

**Mínimo obligatorio antes de declarar `ENTREGA COMPLETA`:**
1. Foundations definidas en `docs/diseno/README.md`: color, tipografía, spacing, radius, border/shadow, states.
2. Tokens implementados en código (sin valores visuales hardcodeados).
3. Componentes base extraídos si ya hay repetición real en la UI.
4. Componentes base documentados en `docs/diseno/componentes/`.

**Regla de cierre dura:**
Si hay UI nueva Y `docs/diseno/README.md` sigue con foundations vacías, o las decisiones visuales relevantes quedaron solo en código → **ENTREGA COMPLETA bloqueada. Declarar ENTREGA PARCIAL.**

**Anti-sobreingeniería:**
No crear design system completo por defecto. Solo materializar la capa mínima que la UI actual ya justifica. No abstraer componentes que todavía no sean patrón real.

## Protocolo: PRDs extensos

Si el PRD activo (snapshot) tiene muchas secciones o es muy largo:

1. Leer primero las secciones 1-4 (visión, problema, usuarios, alcance) para entender el propósito.
2. Luego leer los requisitos funcionales y no funcionales.
3. Luego leer stack, modelo de datos y flujos según la tarea concreta.
4. No perder de vista el alcance general mientras se trabaja en una parte específica.
5. Si se detectan ambigüedades o huecos, preguntar antes de asumir.

## Protocolo: Cambios posteriores al PRD

1. El PRD fundacional no se modifica para incorporar cambios nuevos.
2. Los cambios nuevos se registran en `docs/cambios/` con la plantilla.
3. Cada cambio debe vincularse a: motivo, área afectada, impacto, supuestos y riesgos.
4. Si un cambio contradice el PRD o una decisión previa, crear un ADR nuevo que lo documente.
5. Actualizar el índice en `docs/cambios/README.md`.

## Qué se considera cambio grande

Un cambio es grande si cumple al menos uno de estos criterios:
- Afecta más de 3 archivos en áreas diferentes
- Cambia la arquitectura o estructura del proyecto
- Modifica el modelo de datos
- Introduce o remueve una dependencia importante
- Cambia el comportamiento de un flujo principal
- Contradice una decisión previa

Los cambios grandes requieren: ADR + changelog detallado + verificación explícita.

## Reglas duras — NUNCA hacer esto

1. NUNCA inventar APIs, endpoints, funciones o dependencias que no existan en el proyecto.
2. NUNCA asumir que un archivo existe sin verificarlo.
3. NUNCA importar paquetes que no estén instalados.
4. NUNCA cerrar un cambio dejando el proyecto roto sin declararlo.
5. NUNCA improvisar arquitectura cuando ya existe una documentada.
6. NUNCA usar `PRD.md` para incorporar cambios de alcance posteriores (eso va en `docs/cambios/`).
7. NUNCA duplicar componentes o lógica que ya existe.
8. NUNCA hardcodear secretos, credenciales o API keys.
9. NUNCA ignorar decisiones previas sin crear una nueva que las reemplace.
10. NUNCA crear archivos fuera de la estructura esperada sin justificación.
11. NUNCA ejecutar un PRD real ni crear snapshots PRD cuando el `origin` sea `skay20/VibeRepo`.

## Definition of Done

Una tarea está terminada cuando:
- [ ] El requisito del PRD o change request se cumple
- [ ] El proyecto compila y corre
- [ ] Los tests existentes pasan
- [ ] Se creó ADR si hubo decisión no trivial
- [ ] Se actualizó `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado)
- [ ] Se actualizó documentación afectada
- [ ] Se resolvió fuente PRD y se actualizó `PRD.md` (solo derivado, si fue inicio de proyecto o tarea grande)
- [ ] Se etiquetó el cierre como `ENTREGA COMPLETA` o `ENTREGA PARCIAL`
- [ ] Se incluyó Matriz de cobertura PRD (si fue tarea grande o PRD completo)
- [ ] Si fue `ENTREGA PARCIAL`, se documentaron fases, bloqueos y siguiente acción
- [ ] Se declaró qué se verificó y qué no (verificado/no verificado)
- [ ] Se respetó el design system (si aplica)
- [ ] El repo quedó igual o más ordenado que antes

## Qué leer primero (resumen rápido)

| Prioridad | Archivo | Propósito |
|-----------|---------|-----------|
| 1 | Detección por `origin` | Determinar si estás en repo base o derivado |
| 2 | docs/operacion/estado-sesion.md | Estado actual del proyecto |
| 3 | docs/operacion/fuente-prd.md | Contrato de fuente PRD (solo derivado) |
| 4 | PRD.md | Manifiesto del PRD activo (solo derivado) |
| 5 | docs/contexto/prd-fuentes/(snapshot activo) | PRD fundacional (solo derivado) |
| 6 | docs/contexto/README.md | Entender stack y entorno |
| 7 | docs/decisiones/README.md | Conocer decisiones previas |
| 8 | docs/cambios/README.md | Ver evolución post-PRD |
| 9 | FRAMEWORK_CHANGELOG.md (base) o CHANGELOG.md (derivado) | Historia reciente |
| 10 | docs/diseno/README.md | Design system (si hay UI) |
| 11 | docs/run/README.md | Cómo ejecutar el proyecto |
| 12 | docs/operacion/contrato-ejecucion.md | Contrato anti-skip y formato de cierre |
| 13 | docs/arquitectura/README.md | Reglas de arquitectura |
| 14 | docs/qa/checklist.md | Checks de calidad |
