# VibeRepo — Base Clonable de Proyecto

Repositorio base para iniciar cualquier proyecto desde un PRD, con gobernanza clara, memoria persistente, documentación viva y soporte de primera clase para **Codex** y **Claude**.

---

## Qué es esto

Una plantilla reusable que resuelve el problema de arrancar proyectos sin estructura, sin memoria y sin consistencia. Al clonar este repo obtenés:

- Instrucciones operativas para Codex (AGENTS.md) y Claude (CLAUDE.md)
- Flujo PRD por referencia (ruta/adjunto/URL) sin copy/paste manual
- Skill/agente `framework-sanitizer` para sanear drift documental del repo base
- Sistema de decisiones con ADRs
- Gestión de cambios post-PRD
- Contrato de ejecución anti-skip (entrega completa/parcial + cobertura PRD)
- Gobernanza de diseño para proyectos con UI
- Guía de arquitectura y buenas prácticas
- QA y checklists de verificación
- Changelog estructurado
- Estado ejecutable documentado
- Estructura para especialidades/subagentes futuros

## Repo base vs repo derivado

- `FRAMEWORK_CHANGELOG.md` = historial del repo base (`skay20/VibeRepo`).
- `CHANGELOG.md` = historial del proyecto derivado (template al clonar).

## Cómo usar

### 1. Clonar el repo

```bash
git clone https://github.com/skay20/VibeRepo.git mi-nuevo-proyecto
cd mi-nuevo-proyecto
rm -rf .git
git init
```

### 2. Referenciar el PRD (recomendado)

Iniciar con un prompt en lenguaje natural que incluya referencia explícita al PRD:

```text
Ejecuta este PRD: /ruta/absoluta/al/archivo.md
```

También puede ser ruta relativa, adjunto o URL.
El contrato está en `docs/operacion/fuente-prd.md`.

Después de resolver la fuente, el agente debe:
- guardar snapshot en `docs/contexto/prd-fuentes/`
- actualizar `PRD.md` (fuente activa + última ingesta + snapshot)

`PRD-template.md` queda disponible como plantilla opcional si querés redactar PRD dentro del repo.

### 3. Completar el contexto

Llenar `docs/contexto/README.md` con stack, entorno, integraciones y restricciones.
Si el stack no está definido, dejarlo vacío — el modelo preguntará antes de asumir.

### 4. Definir ubicación de implementación

Por defecto, el código de producto nuevo vive en `product/`.

Ejemplo:

```bash
mkdir -p product
cd product
```

Si usás otra estructura (ej. `apps/<slug>`), documentá la excepción en `docs/decisiones/` o `docs/cambios/`.

### 5. Arrancar con Codex o Claude

- **Codex** lee `AGENTS.md` automáticamente.
- **Claude** lee `CLAUDE.md` automáticamente.
- Ambos están instruidos para leer el PRD, decisiones, contexto y contrato anti-skip antes de actuar.
- Para sanear el repo base VibeRepo después de cambios de gobernanza:
  - Codex: `Usa la skill framework-sanitizer y sanea el repo base`
  - Claude: `Usa framework-sanitizer para revisar drift del repo base`

### 6. Evolucionar el proyecto

- Nuevos cambios → `docs/cambios/` (usar la plantilla)
- Decisiones importantes → `docs/decisiones/` (usar la plantilla ADR)
- Cambios de UI → verificar `docs/diseno/README.md`
- Cierres grandes → declarar `ENTREGA COMPLETA/PARCIAL` + matriz de cobertura PRD
- Cada cambio → actualizar `CHANGELOG.md`

> En el repo base VibeRepo, los cambios del framework se registran en `FRAMEWORK_CHANGELOG.md`.

## Estructura del repo

```
README.md                              ← Este archivo
AGENTS.md                              ← Instrucciones operativas para Codex
CLAUDE.md                              ← Instrucciones operativas para Claude
PRD.md                                 ← Manifiesto operativo del PRD activo
PRD-template.md                        ← Plantilla opcional de PRD completo
FRAMEWORK_CHANGELOG.md                 ← Historial del framework base (VibeRepo)
CHANGELOG.md                           ← Historial del proyecto derivado
.gitignore                             ← Ignores multi-stack
.claude/
├── settings.json                      ← Permisos operativos de Claude (allow/deny)
└── agents/
    └── framework-sanitizer.md         ← Wrapper del agente Claude para sanear el framework base

docs/
├── contexto/
│   ├── README.md                      ← Stack, entorno, integraciones, restricciones
│   └── prd-fuentes/                   ← Snapshots versionados del PRD referenciado
│       └── README.md                  ← Convención de ingesta PRD
├── decisiones/                        ← ADRs y memoria de decisiones
│   ├── README.md                      ← Índice maestro + reglas de uso
│   ├── _template-adr.md               ← Plantilla de ADR
│   ├── 0001-adoptar-vibeRepo.md       ← ADR semilla
│   ├── 0002-convencion-carpeta-product.md  ← Política de carpeta product/
│   └── 0003-prd-por-referencia-con-snapshot.md ← Política de PRD por referencia
├── cambios/                           ← Change requests post-PRD
│   ├── README.md                      ← Índice y guía
│   └── _template-cambio.md            ← Plantilla de change request
├── arquitectura/README.md             ← Guía de arquitectura y buenas prácticas
├── operacion/                         ← Gobernanza operativa compartida
│   ├── fuente-prd.md                  ← Contrato de referencia e ingesta PRD
│   ├── contrato-ejecucion.md          ← Contrato anti-skip + Matriz PRD
│   ├── gate-release.md                ← Checklist pre-merge/release por tier
│   └── estado-sesion.md               ← Snapshot del proyecto (actualizar por sesión)
├── qa/                                ← QA y verificación
│   ├── README.md                      ← Guía de QA
│   └── checklist.md                   ← Checklist pre-entrega
├── diseno/                            ← Design system (si hay UI)
│   ├── README.md                      ← Gobernanza + foundations + checklist visual
│   ├── _template-componente.md        ← Plantilla para documentar un componente
│   ├── componentes/                   ← [nombre-componente].md por componente
│   ├── paginas/                       ← [nombre-pagina].md por layout/página
│   └── decisiones/                    ← ADRs de diseño (separados de los técnicos)
├── run/README.md                      ← Setup, ejecución, errores conocidos
└── especialidades/                    ← Subagentes/skills futuros
    ├── README.md                      ← Guía + preguntas para definirlos
    ├── _template-especialidad.md      ← Plantilla de especialidad
    └── framework-sanitizer.md         ← Protocolo neutral de sanitización del framework

product/                               ← Convención por defecto para código de producto
├── README.md                          ← Setup operativo del producto derivado
                                          (crear/completar al iniciar implementación)

skills/
└── framework-sanitizer/
    └── SKILL.md                       ← Skill Codex para sanear drift documental del framework base
```

## Principios

1. **Multi-LLM**: Funciona con Codex y Claude con gobernanza alineada
2. **PRD-first**: Todo proyecto empieza desde un PRD
3. **Memoria persistente**: Decisiones registradas, nunca contradecir sin rastro
4. **Gobernanza simple**: Reglas claras, no burocracia
5. **Running-first**: El proyecto siempre debe quedar ejecutable
6. **No-skip**: Cierre explícito (`ENTREGA COMPLETA/PARCIAL`) + cobertura PRD en tareas grandes
7. **Diseño gobernado**: Consistencia visual, reuse-first (si hay UI)
8. **Documentación viva**: Se mantiene actualizada, no se crea y abandona
9. **Evolución continua**: Acepta cambios post-PRD sin caos

## Qué NO es este repo

- No es un framework de agentes
- No es una plataforma de workflows
- No impone un stack fijo
- No tiene gates pesados ni automatizaciones frágiles
- No genera burocracia innecesaria

## Licencia

(definir según el proyecto)
