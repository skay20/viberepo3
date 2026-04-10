# Componente: Card

## Propósito
Contenedor reusable para bloques de contenido con jerarquía visual consistente.

## Ubicación
- Archivo: `product/intake-form/src/components/ui/card.jsx`
- Exportado desde: `Card`, `CardHeader`, `CardTitle`, `CardDescription`, `CardContent`, `CardFooter`

## Props / API

| Prop | Tipo | Default | Descripción |
|------|------|---------|-------------|
| `className` | `string` | `""` | Ajustes visuales adicionales |
| `...props` | `div props` | — | Props nativas del contenedor |

## Variantes
- Base reusable con subslots (`Header`, `Content`, `Footer`)

## Estados
- Default

## Tokens utilizados
- Color: `card`, `card-foreground`, `border`
- Spacing: `p-6`, `pt-0`
- Typography: `font-heading` en títulos
- Border/Shadow: `rounded-xl`, `shadow-sm`

## Uso

```jsx
<Card>
  <CardHeader>
    <CardTitle>Titulo</CardTitle>
  </CardHeader>
  <CardContent>Contenido</CardContent>
</Card>
```

## Dónde se usa
- Resumen ejecutivo
- Estado del progreso
- Tarjetas de preview y confirmación

## Restricciones
- No usar para layout global completo si solo se necesita un wrapper simple.

## Decisiones relacionadas
- ADR: [0005]

## Notas de accesibilidad
- Mantener estructura semántica interna cuando represente contenido agrupado relevante.
