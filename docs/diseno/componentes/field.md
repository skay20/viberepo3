# Componente: Field

## Propósito
Estandarizar inputs y textareas con label, estado de error y accesibilidad básica.

## Ubicación
- Archivo: `product/intake-form/src/components/Field.jsx`
- Base visual para inputs simples: `product/intake-form/src/components/ui/input.jsx`
- Exportado desde: `Field`

## Props / API

| Prop | Tipo | Default | Descripción |
|------|------|---------|-------------|
| `id` | `string` | — | Identificador del campo |
| `label` | `string` | — | Texto de etiqueta |
| `value` | `string` | — | Valor controlado |
| `onChange` | `function` | — | Handler de cambio |
| `required` | `boolean` | `false` | Marca campo obligatorio |
| `error` | `string` | `""` | Mensaje de validación |
| `placeholder` | `string` | — | Placeholder |
| `type` | `string` | `"text"` | Tipo input (`email`, `number`, etc.) |
| `multiline` | `boolean` | `false` | Usa `textarea` |
| `rows` | `number` | `4` | Altura de `textarea` |

## Variantes
- Input simple
- Textarea (`multiline=true`)

## Estados
- Default
- Focus
- Error

## Tokens utilizados
- Color: `panel-soft`, `ink`, `muted`, `border`, `accent`, `danger`
- Spacing: `px-5`, `py-4`
- Typography: `text-sm`, labels en mayúscula con tracking amplio
- Border/Shadow: `rounded-[22px]`, inset sutil + `shadow-focus`

## Uso

```jsx
<Field
  id="email"
  label="Email"
  required
  value={email}
  onChange={onEmailChange}
  error={errors.email}
  type="email"
/>
```

## Dónde se usa
- Todos los pasos del formulario

## Restricciones
- Siempre debe renderizar `label` visible.
- Errores deben venir desde validación de dominio, no del componente.
- No usar placeholders como sustituto de labels ni ocultar el focus ring.

## Decisiones relacionadas
- ADR: [0004]
- ADR: [0005]

## Notas de accesibilidad
- `label` asociado por `htmlFor`
- `aria-invalid` y `aria-describedby` cuando hay error
