# Gobernanza de Diseño y Design System

Reglas para mantener consistencia visual y estructural en proyectos con UI relevante.

> Si el proyecto no tiene frontend ni capa visual significativa, este documento se marca como **No Aplica** y no impone carga alguna.

---

## Regla de cierre para LLMs (leer antes de implementar UI)

### Trigger
Esta regla se activa si la tarea:
- Crea la **primera UI real** del proyecto, o
- Introduce un **patrón visual nuevo relevante**

### Mínimo obligatorio antes de `ENTREGA COMPLETA`
- Foundations completadas en este archivo (sección Foundations más abajo): color, tipografía, spacing, radius, border/shadow, states
- Tokens implementados en código — sin valores hardcodeados como `#19e6c4` o `24px` sueltos
- Componentes base extraídos si ya hay repetición real (mismo patrón en 2+ lugares)
- Componentes base documentados en `docs/diseno/componentes/[nombre].md`

### Regla de cierre dura
Si hay UI nueva Y esta sección de Foundations sigue vacía, o las decisiones visuales relevantes quedaron solo embebidas en el código sin documentar → **`ENTREGA COMPLETA` bloqueada. Declarar `ENTREGA PARCIAL`.**

### Anti-sobreingeniería
No materializar un design system completo por defecto.
Solo construir la capa mínima que la UI actual ya justifica.
No abstraer componentes que todavía no sean un patrón real repetido.

---

## Principios obligatorios

### 1. Reuse primero
- Nunca crear UI nueva sin revisar si ya existe componente, variante o patrón reusable
- Si un patrón aparece por segunda vez, evaluar explícitamente para promoción
- Si un patrón aparece por tercera vez, promover a componente compartido (salvo justificación documentada)

### 2. Consistencia visual
- Evitar valores visuales hardcodeados cuando puedan resolverse con tokens o variables
- Si el stack tiene tokens implementados, la documentación debe alinearse con la implementación real
- Si el stack aún no los tiene, definir al menos convenciones para: color, spacing, radius, border, shadow, tipografía, estados y layout

### 3. Documentación viva
- Todo componente reusable debe quedar documentado: copiar `_template-componente.md` y guardarlo como `componentes/[nombre-componente].md`
- Todo layout o pantalla reutilizable debe documentarse en `paginas/[nombre-pagina].md`
- Toda excepción visual relevante debe quedar registrada en `docs/diseno/decisiones/[descripcion].md` (separado de los ADRs técnicos en `docs/decisiones/`)
- Todo cambio estructural del sistema visual debe dejar una decisión documentada
- La documentación del design system es fuente de verdad y debe mantenerse alineada con el código

### 4. Definition of Done para UI
Un cambio de UI no está terminado si no incluye (cuando corresponda):
- Validación o actualización del patrón reusable
- Documentación del componente o flujo afectado
- Nota de impacto visual
- Excepción documentada si rompe o extiende una regla existente

### 5. No caos
- No crear estilos locales arbitrarios sin comparar con el sistema existente
- No duplicar componentes con nombres distintos para resolver el mismo problema
- No crear variantes innecesarias
- No dejar decisiones visuales solo en código si afectan el sistema de diseño

## Estructura del design system

```
docs/diseno/
├── README.md                         # Este archivo - gobernanza general
├── _template-componente.md            # Plantilla para documentar componentes
├── componentes/                       # Un .md por componente: [nombre].md
├── paginas/                           # Un .md por layout o pantalla: [nombre].md
└── decisiones/                        # Decisiones de diseño (no ADRs técnicos)
                                       # Formato libre, nombrar: [descripcion].md
```

> **Separación de decisiones:**
> - `docs/diseno/decisiones/` → excepciones visuales, patrones nuevos, elecciones de design system
> - `docs/decisiones/` → ADRs técnicos, de producto o de arquitectura
> No mezclar. Una excepción visual no es un ADR técnico.

## Foundations (completar cuando se defina el stack)

### Colores
- Primario: `--color-primary` `#1c1917`
- Primario fuerte (hover): `--color-primary-strong` `#2b2724`
- Acento premium: `--color-accent` `#a16207`
- Acento suave: `--color-accent-soft` `rgba(161, 98, 7, 0.10)`
- Superficie base: `--color-surface` `#f5f1ea`
- Panel/contenedor: `--color-panel` `rgba(255, 251, 247, 0.82)`
- Texto principal: `--color-ink` `#171411`
- Texto secundario: `--color-muted` `#6b6259`
- Borde: `--color-border` `#d8cfc4`
- Semánticos: `--color-danger` `#b42318`, `--color-success` `#1f6d43`

### Tipografía
- Heading: `Playfair Display`, pesos `500/600/700`
- Body: `Inter`, pesos `300/400/500/600/700`
- Dirección: editorial sobria, con serif de alto contraste para titulares y sans neutra para legibilidad de formulario
- Escala base usada: `text-xs`, `text-sm`, `text-base`, `text-lg`, `text-2xl`, `text-4xl`, `text-5xl`, `text-6xl`

### Espaciado
- Tokens CSS: `--space-1/2/3/4/5/6/8/10/12`
- Equivalencias: `4, 8, 12, 16, 20, 24, 32, 40, 48 px`

### Bordes y sombras
- Radius: `--radius-sm` `12px`, `--radius-md` `16px`, `--radius-lg` `24px`, `--radius-xl` `32px`
- Border width base: `1px`
- Sombra principal panel: `--shadow-panel` `0 28px 80px rgba(23, 20, 17, 0.12)`
- Sombra de foco: `--shadow-focus` `0 0 0 3px rgba(161, 98, 7, 0.22)`

### Estados
- Default: variante base por componente
- Hover: `primary -> primary-strong`, secundarios elevan contraste y borde con acento oro
- Focus: `shadow-focus` consistente en campos y botones
- Disabled: `opacity-60` + `cursor-not-allowed`
- Error: borde/mensaje `danger`
- Loading: no implementado en esta fase (N/A)

## Componentes documentados
- `docs/diseno/componentes/button.md`
- `docs/diseno/componentes/card.md`
- `docs/diseno/componentes/field.md`
- `docs/diseno/componentes/stepper.md`

## Checklist de revisión visual
Antes de cerrar un cambio de UI:
- [ ] ¿Se revisó el design system antes de crear algo nuevo?
- [ ] ¿Se reutilizaron componentes existentes?
- [ ] ¿Los valores visuales usan tokens o variables?
- [ ] ¿La UI es consistente con el resto del proyecto?
- [ ] ¿Se documentó el componente nuevo o la excepción?
- [ ] ¿Se consideró accesibilidad básica?
