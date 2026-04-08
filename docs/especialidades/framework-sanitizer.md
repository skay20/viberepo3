# Especialidad: Framework Sanitizer

## Proposito
Sanear drift y gaps de documentacion del **repo base VibeRepo** despues de cambios en gobernanza, arquitectura operativa o contratos del framework.

Esta especialidad existe porque las instrucciones generales de `AGENTS.md` y `CLAUDE.md` no alcanzan para garantizar, por si solas, que README, changelog de framework, QA, contratos y referencias cruzadas queden siempre alineados.

## Tipo
Documentacion neutral | Skill Codex | Agente Claude

## Cuando se usa
- Trigger: cambios en `AGENTS.md`, `CLAUDE.md`, `README.md`, `FRAMEWORK_CHANGELOG.md`, `docs/operacion/`, `docs/qa/`, `docs/arquitectura/` o decisiones del framework.
- Frecuencia esperada: al final de cada cambio relevante del repo base y antes de mergear a `main`.

## Que debe leer antes de actuar
- Archivos del repo:
  - `AGENTS.md`
  - `CLAUDE.md`
  - `README.md`
  - `FRAMEWORK_CHANGELOG.md`
  - `docs/qa/checklist.md`
  - `docs/qa/README.md`
  - `docs/operacion/contrato-ejecucion.md`
  - `docs/operacion/gate-release.md`
  - `docs/operacion/fuente-prd.md`
  - `docs/arquitectura/README.md`
  - `docs/decisiones/README.md`
- Documentacion:
  - `docs/especialidades/README.md`
- Decisiones previas:
  - ADRs del framework en `docs/decisiones/`

## Que debe producir
- Output principal:
  - diagnostico corto de drifts/gaps encontrados
  - correcciones documentales necesarias
  - verificacion final de consistencia
- Actualizaciones a documentacion:
  - archivos de gobernanza afectados
  - `FRAMEWORK_CHANGELOG.md`
- Decisiones a registrar:
  - ADR solo si la skill obliga a cambiar politica del framework, no para correcciones menores de consistencia

## Que NO debe hacer
- No modificar codigo de producto.
- No ejecutar PRDs ni crear snapshots en `docs/contexto/prd-fuentes/`.
- No actualizar `CHANGELOG.md` de proyecto derivado cuando esta trabajando en el repo base.
- No inventar nuevas politicas si basta con alinear las existentes.

## Limites
- No puede modificar secretos o configuracion sensible.
- No puede cambiar contratos del framework sin dejar trazabilidad en `FRAMEWORK_CHANGELOG.md`.
- Maximo alcance por ejecucion: documentacion del repo base y referencias cruzadas asociadas.

## Inputs requeridos

| Input | Tipo | Obligatorio | Descripcion |
|-------|------|-------------|-------------|
| modo esperado | texto | No | Normalmente `repo base`; si no se pasa, detectar por `origin` |
| alcance | texto | No | Opcional: archivos o areas cambiadas |
| objetivo | texto | No | Ej: "sanear despues de cambio de PRD por referencia" |

## Outputs esperados

| Output | Formato | Destino |
|--------|---------|---------|
| drifts encontrados | lista corta | respuesta final |
| correcciones aplicadas | lista corta | respuesta final |
| trazabilidad de framework | entrada de changelog | `FRAMEWORK_CHANGELOG.md` |
| verificacion final | verificado/no verificado | respuesta final |

## Protocolo operativo
1. Detectar modo por `origin`. Si no es repo base, detenerse salvo pedido explicito del usuario.
2. Revisar contratos principales y buscar inconsistencias de nombres, rutas, semantica base/derivado y obligaciones de cierre.
3. Priorizar correccion de drift en este orden:
   - reglas de modo base/derivado
   - `README.md`
   - `FRAMEWORK_CHANGELOG.md`
   - QA y gate docs
   - contratos operativos
4. Corregir solo lo necesario para restaurar consistencia; no expandir alcance por gusto.
5. Registrar el cambio del framework en `FRAMEWORK_CHANGELOG.md`.
6. Verificar con busquedas que no quedaron referencias obsoletas a rutas, nombres o contratos previos.

## Reglas de anti-hallucination
- No inventar archivos, APIs o dependencias que no existan en el repo.
- No asumir que una referencia esta actualizada: verificarla.
- No reportar repo sano sin chequear al menos README, AGENTS, CLAUDE, changelog y QA.

## Definition of Done
- [ ] Se detecto correctamente si el repo es base o derivado
- [ ] Se corrigieron drifts documentales relevantes del repo base
- [ ] `FRAMEWORK_CHANGELOG.md` refleja el ultimo cambio de framework
- [ ] No quedaron referencias obsoletas criticas en contratos, QA o README
