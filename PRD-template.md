# PRD Template (Opcional)

Usar esta plantilla solo si querés redactar el PRD completo dentro del repo.
Flujo recomendado del framework: referenciar PRD por prompt + snapshot en `docs/contexto/prd-fuentes/`.

---

## 1. Visión

¿Qué se quiere construir y por qué?

## 2. Problema
¿Qué problema concreto resuelve este proyecto?
¿Para quién?

## 3. Usuarios objetivo
¿Quiénes van a usar esto?
¿Qué necesitan?
¿Qué nivel técnico tienen?

## 4. Alcance inicial
¿Qué se incluye en la primera versión?
¿Qué se excluye explícitamente?

### Dentro del alcance
- ...

### Fuera del alcance
- ...

## 5. Requisitos funcionales
Listar como items verificables, no como prosa vaga.

- [ ] RF-001: ...
- [ ] RF-002: ...
- [ ] RF-003: ...

## 6. Requisitos no funcionales
Performance, seguridad, accesibilidad, compatibilidad, etc.

- [ ] RNF-001: ...
- [ ] RNF-002: ...

## 7. Stack tecnológico
Si no está definido, dejar vacío. No inventar stack arbitrario.

- Frontend:
- Backend:
- Base de datos:
- Infraestructura:
- Otros:

## 7.1 Ubicación de implementación

Convención por defecto: código de producto en `product/`.

Si se usa otra estructura, documentar excepción:
- Estructura alternativa: `apps/<slug>` | otra: ...
- Justificación: ...
- Decisión registrada en: ADR NNNN o `docs/cambios/CR-NNNN`

## 8. Modelo de datos
Entidades principales y relaciones (alto nivel).

## 9. Pantallas / Flujos principales
Si no hay UI, marcar como no aplica.

### Flujo A: [nombre]
1. ...
2. ...
3. ...

### Flujo B: [nombre]
1. ...
2. ...

## 10. Integraciones
APIs, servicios externos, SDKs, autenticación.

## 11. Restricciones
Límites técnicos, regulatorios, tiempo, presupuesto, equipo.

## 12. Riesgos conocidos
¿Qué podría salir mal?
¿Qué dependencias externas son críticas?

## 13. Entregables esperados
¿Qué debe existir al final de la primera versión?

- [ ] ...
- [ ] ...

## 14. Criterios de aceptación
¿Cómo se sabe que el proyecto está terminado?

## 15. Preguntas abiertas
- [ ] ...
- [ ] ...

## 16. Evolución futura
- ...
- ...
