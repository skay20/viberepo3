# Componente: Stepper

## Propósito
Mostrar progreso del formulario multi-step con estado visual de paso actual y completados.

## Ubicación
- Archivo: `product/intake-form/src/components/Stepper.jsx`
- Exportado desde: `Stepper`

## Props / API

| Prop | Tipo | Default | Descripción |
|------|------|---------|-------------|
| `steps` | `Array<{id,title}>` | — | Definición de pasos |
| `currentStep` | `number` | — | Paso actual (1-indexado) |

## Variantes
- Default (grid responsive 2 columnas mobile / 4 desktop)

## Estados
- Pendiente
- Activo
- Completado

## Tokens utilizados
- Color: `primary`, `accent`, `success`, `border`, `panel`, `ink`, `muted`
- Spacing: `px-3`, `py-2`, `gap-3`
- Typography: `text-xs`, `text-sm`
- Border/Shadow: `rounded-[24px]`

## Uso

```jsx
<Stepper steps={STEPS} currentStep={currentStep} />
```

## Dónde se usa
- Header del formulario multi-step

## Restricciones
- No usar para workflows con navegación no lineal sin extensión explícita.

## Decisiones relacionadas
- ADR: [0004]

## Notas de accesibilidad
- `aria-label="Progreso del formulario"` en el contenedor
