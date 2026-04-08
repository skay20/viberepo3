# Gestión de Cambios

Sistema para evolucionar el proyecto después del PRD inicial sin perder contexto ni orden.

## Propósito
El PRD.md es el documento fundacional del proyecto. No debe reescribirse cada vez que aparece un cambio.
Los cambios posteriores se registran aquí como change requests, feature requests, bug fixes o refactors.

## Cómo registrar un cambio
1. Copiar `_template-cambio.md`
2. Nombrar como `CR-NNNN-slug.md` (change request) o `FR-NNNN-slug.md` (feature request)
3. Completar todas las secciones relevantes
4. Vincular a decisiones existentes si el cambio las afecta

## Qué registrar aquí
- Nuevas features que no estaban en el PRD
- Cambios de alcance o prioridad
- Refactors grandes
- Bugs relevantes que impliquen decisiones
- Extensiones o integraciones nuevas

## Qué NO registrar aquí
- Bugs triviales (usar issues o tracker)
- Cambios cosméticos menores
- Ajustes que no afectan arquitectura, producto ni diseño

## Reglas
- Cada cambio debe vincularse al contexto existente (PRD, decisiones, diseño)
- Si un cambio contradice una decisión previa, debe crearse una nueva decisión en docs/decisiones/
- El changelog debe actualizarse cuando el cambio se implemente
- Ningún cambio grande debe parecer que empieza desde cero

## Índice de cambios

| # | Título | Tipo | Estado | Fecha |
|---|--------|------|--------|-------|
| (vacío - se llena con el primer cambio) |
