# Estado Ejecutable del Proyecto

Este documento define qué significa que el proyecto "corra" y registra el estado actual de ejecución.

---

## Setup

### Prerequisitos
- Node.js 20+
- npm 10+

### Instalación
```bash
cd product/intake-form
npm install
```

### Variables de entorno
- No requiere variables para la fase actual.

### Ejecución
```bash
cd product/intake-form
npm run dev
```

### Build
```bash
cd product/intake-form
npm run build
```

### Tests
```bash
cd product/intake-form
npm run lint
```

## Criterios mínimos de "esto corre"
- [x] Se instalan las dependencias sin errores
- [x] El proyecto se levanta sin errores fatales
- [x] La ruta principal responde
- [x] No hay errores bloqueantes en consola/logs
- [x] Los checks existentes (`lint`) pasan

## Estado actual

| Aspecto | Estado | Notas |
|---------|--------|-------|
| Instalación | verificado | `npm install` exitoso |
| Ejecución | verificado | `npm run dev` disponible |
| Build | verificado | `npm run build` exitoso |
| Tests | parcial | no hay test runner, se usa `lint` |

## Errores conocidos

| Error | Impacto | Workaround | Fecha |
|-------|---------|------------|-------|
| (vacío) | | | |

## Notas
- El proyecto no tiene suite de tests automatizados todavía.
