# Componente: Button

## Propósito
Acción primaria/secundaria consistente para navegación del formulario y CTAs.

## Ubicación
- Archivo: `product/intake-form/src/components/Button.jsx`
- Base visual: `product/intake-form/src/components/ui/button.jsx`
- Exportado desde: `Button`

## Props / API

| Prop | Tipo | Default | Descripción |
|------|------|---------|-------------|
| `variant` | `"primary" | "secondary"` | `"primary"` | Estilo visual del botón |
| `className` | `string` | `""` | Clases extra opcionales |
| `...props` | `button props` | — | `type`, `onClick`, `disabled`, etc. |

## Variantes
- Default: `primary`
- Secundaria: `secondary`

## Estados
- Default
- Hover
- Focus
- Disabled

## Tokens utilizados
- Color: `primary`, `primary-strong`, `accent`, `border`, `ink`, `panel`
- Spacing: `px-6`, `py-3`
- Typography: `text-sm`, `font-semibold`, `tracking-[0.08em]`, `uppercase`
- Border/Shadow: `rounded-full`, `shadow-focus`

## Uso

```jsx
<Button type="button">Siguiente</Button>
<Button type="button" variant="secondary">Atrás</Button>
```

## Dónde se usa
- Pantalla intro
- Footer de navegación de pasos
- Pantalla de confirmación

## Restricciones
- No usar como enlace externo (usar `<a>` cuando corresponda).
- No agregar colores inline fuera de tokens.

## Decisiones relacionadas
- ADR: [0004]
- ADR: [0005]

## Notas de accesibilidad
- Focus visible obligatorio
- `disabled` semántico cuando no se puede navegar
