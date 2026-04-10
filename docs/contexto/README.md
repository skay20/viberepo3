# Contexto del Proyecto

Este archivo describe el contexto operativo del proyecto: stack, entorno, integraciones y restricciones.

---

## Nombre del proyecto
Candidate Intake Form

## Descripción breve
Aplicación frontend para intake de candidatos con flujo guiado de 4 pasos, validaciones obligatorias y confirmación final.

## Stack tecnológico

- Frontend: React 19 + Vite 8 + Tailwind CSS 3.4 + shadcn/ui (integracion incremental)
- Backend: No aplica (fase actual)
- Base de datos: No aplica (fase actual)
- Infraestructura: Ejecución local con Node.js
- Otros: ESLint, class-variance-authority, clsx, tailwind-merge, Lucide

## Estado de gobernanza

- El repositorio actual opera como **repo derivado** según `origin`.
- La gobernanza base sigue viniendo de `AGENTS.md`, `CLAUDE.md`, `PRD.md` y `docs/`.
- La guía visual activa del frontend está en `product/intake-form/DESIGN.md`.

## Entorno de ejecución
- Local: `product/intake-form`
- Staging: No configurado
- Producción: Build estático (pendiente de hosting)

## Integraciones externas
(APIs, servicios terceros, SDKs)

- Ninguna en esta fase

## Restricciones conocidas

- Todo client-side
- Sin persistencia en backend ni base de datos
- Sin autenticación
- Sin integración ATS

## Variables de entorno requeridas

| Variable | Propósito | Obligatoria |
|----------|-----------|-------------|
| No aplica | No se requieren variables en esta fase | No |

## Scripts disponibles

| Comando | Propósito |
|---------|-----------|
| `npm run dev` | Ejecuta app en desarrollo |
| `npm run build` | Genera build de producción |
| `npm run preview` | Sirve build localmente |
| `npm run lint` | Ejecuta análisis estático |

## Notas
- La implementación vive en `product/intake-form/` siguiendo ADR 0002.
- Decisión de stack registrada en ADR 0004.
- La dirección visual activa quedó formalizada en ADR 0006 y en `docs/diseno/decisiones/elevenlabs-adapted-product-direction.md`.
