# Snapshot PRD

- Fuente original: /Users/matiassouza/Desktop/Prds Creados/PRDsimple.md
- Fecha de ingesta: 2026-04-08 14:14 CEST
- Ingerido por: Codex
- Identificador de contenido (sha256): a554a962d2b88b67c22d5789de31d47fff10b91a19e3c03be5fee6ce1846d56c
- Notas de alcance: Implementación completa de feature frontend multi-step en repo derivado.

---

PRD — Multi-step Candidate Intake Form


Criterio de selección: Nueva feature completa con UI, lógica de validación y navegación multi-step
Qué activa: Validaciones obligatorias, manejo de estado entre pasos, UX consistente, navegación controlada
1. Visión

Construir un formulario web moderno de 4 pasos para intake de candidatos que permita recolectar información estructurada de forma progresiva, con una experiencia fluida, validaciones estrictas y una interfaz clara y agradable.

El objetivo es maximizar la tasa de completitud y calidad de los datos recolectados.

2. Problema

Los formularios largos generan abandono y errores en la carga de datos.

Se necesita:

Dividir la carga en pasos claros
Forzar completitud de campos obligatorios
Mejorar la experiencia visual y fluidez

Para equipos de recruiting o selección que necesitan intake limpio y consistente.

3. Usuarios objetivo
Candidatos aplicando a posiciones
Nivel técnico: bajo a medio
Necesitan:
Claridad
Rapidez
Feedback inmediato
No cometer errores
4. Alcance inicial
Dentro del alcance
Formulario de 4 pasos
Validación obligatoria por campo
Navegación Next / Back
Animaciones suaves entre pasos
UI moderna con Tailwind CSS
Pantalla inicial (intro)
Pantalla final (confirmación)
Estado persistente en memoria durante la sesión
Fuera del alcance
Backend / persistencia en base de datos
Autenticación
Integración con ATS
Guardado parcial (draft)
Multilenguaje
5. Requisitos funcionales
 RF-001: El sistema debe mostrar una pantalla inicial con CTA para comenzar el formulario
 RF-002: El formulario debe dividirse en 4 pasos claramente definidos
 RF-003: Cada paso debe tener botón “Siguiente” y “Atrás”
 RF-004: No se puede avanzar si los campos obligatorios no están completos
 RF-005: Los campos obligatorios deben mostrar feedback visual claro (error)
 RF-006: El usuario puede volver atrás sin perder los datos ingresados
 RF-007: El estado del formulario debe persistir durante la navegación interna
 RF-008: Transiciones entre pasos deben incluir animaciones suaves
 RF-009: El último paso debe permitir enviar el formulario
 RF-010: Al enviar, se debe mostrar pantalla final de confirmación
 RF-011: Debe existir un indicador de progreso (stepper o similar)
 RF-012: Debe existir un banner o contenedor central que estructura la UI
6. Requisitos no funcionales
 RNF-001: UI responsive (mobile-first)
 RNF-002: Transiciones fluidas (<300ms)
 RNF-003: Accesibilidad básica (labels, focus states)
 RNF-004: Performance: carga instantánea (sin bloqueos)
 RNF-005: Consistencia visual (spacing, typography, color system)
 RNF-006: Feedback visual claro en errores y estados
7. Stack tecnológico
Frontend: React (recomendado, no obligatorio)
UI: Tailwind CSS
State management: local state (useState / equivalent)
Animaciones: Tailwind transitions o Framer Motion
Backend: —
Base de datos: —
Infraestructura: —
7.1 Ubicación de implementación
Estructura: product/intake-form/
Justificación: Feature autocontenida de frontend
Decisión registrada en: docs/cambios/CR-001
8. Modelo de datos

Entidad principal: CandidateForm

Campos (ejemplo):

step1:
nombre
apellido
email
step2:
experiencia laboral
años de experiencia
step3:
habilidades
herramientas
step4:
disponibilidad
expectativa salarial

Estado:

{
  currentStep: number,
  data: {
    step1: {},
    step2: {},
    step3: {},
    step4: {}
  }
}
9. Pantallas / Flujos principales
Flujo A: Inicio → Formulario → Confirmación
Pantalla inicial
Banner central
CTA “Comenzar”
Paso 1
Inputs básicos
Validación obligatoria
Paso 2
Información profesional
Paso 3
Skills
Paso 4
Datos finales
Pantalla final
Confirmación
Mensaje de éxito
10. Integraciones

No aplica en esta fase.

11. Restricciones
Sin backend
Todo client-side
Sin almacenamiento persistente
Solo Tailwind como sistema de estilos
12. Riesgos conocidos
Abandono si UX no es clara
Validaciones mal implementadas → frustración
Animaciones pesadas → degradación de performance
13. Entregables esperados
 UI completa funcional
 Navegación entre pasos estable
 Validaciones obligatorias funcionando
 Animaciones implementadas
 Pantalla inicial y final
 Código organizado en estructura clara
14. Criterios de aceptación
El usuario no puede avanzar sin completar campos obligatorios
El usuario puede navegar atrás sin perder datos
El flujo completo se puede completar sin errores
Las animaciones son suaves y consistentes
La UI es responsive y usable en mobile
El estado se mantiene correctamente durante todo el flujo
15. Preguntas abiertas
 ¿Se definen exactamente los campos por paso?
 ¿Se requiere validación avanzada (email, formatos)?
 ¿Se enviará a API en una siguiente fase?
16. Evolución futura
Guardado automático (draft)
Integración con backend / ATS
Multi idioma
Analytics de completitud
A/B testing de UX
Personalización por tipo de candidato