# Gate: Pre-Release / Pre-Merge

Checkpoint obligatorio antes de mergear a main o hacer un release.
Complementa el contrato de ejecución: el contrato cierra una tarea, el gate aprueba un merge.

> **Cuándo usarlo:**
> - Antes de cualquier merge a `main`
> - Antes de un deploy o release
> - Obligatorio para cambios con tier `strict`
> - Recomendado para cambios con tier `standard` que afecten flujos principales

---

## Artifacts

- [ ] `FRAMEWORK_CHANGELOG.md` (base) o `CHANGELOG.md` (derivado) actualizado con esta entrega
- [ ] ADR creado si hubo decisión de arquitectura, producto o diseño
- [ ] Closure tag aplicado: `ENTREGA COMPLETA` o `ENTREGA PARCIAL`
- [ ] Si fue `ENTREGA PARCIAL`: fases, bloqueos y próximo paso documentados

## Calidad

- [ ] El proyecto compila sin errores
- [ ] Tests pasan (o excepciones documentadas con motivo)
- [ ] No hay secrets, credenciales o API keys hardcodeadas
- [ ] No hay `console.log`, `print` o debug statements innecesarios
- [ ] No hay archivos temporales, TODOs críticos sin issue o código comentado sin motivo

## Según tier

### `lean`
Solo los dos bloques de arriba (artifacts + calidad).

### `standard`
Todo lo anterior, más:
- [ ] QA checklist (`docs/qa/checklist.md`) completado para los ítems relevantes
- [ ] Decisiones nuevas no contradicen decisiones previas en `docs/decisiones/`
- [ ] Documentación actualizada si cambió comportamiento observable
- [ ] Si hubo UI nueva: foundations definidas en `docs/diseno/README.md` y componentes documentados en `docs/diseno/componentes/`

### `strict`
Todo lo anterior, más:
- [ ] Impacto en decisiones existentes documentado explícitamente
- [ ] Riesgos residuales registrados en `docs/run/README.md`
- [ ] Revisión de seguridad básica: inputs validados, sin exposición de datos sensibles
- [ ] Plan de rollback identificado (aunque sea manual)
- [ ] Si hay cambio de DB schema o migración: validado en entorno de staging o equivalente
- [ ] Si hubo UI nueva o patrón visual relevante: tokens implementados en código, sin valores hardcodeados

---

## Resultado

**Estado:** `APROBADO` | `BLOQUEADO`

**Bloqueado por:** (completar si aplica)
- ...

**Aprobado por:** (humano o modelo que completó el gate)

**Fecha:** YYYY-MM-DD
