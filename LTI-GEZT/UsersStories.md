# 🚀 Backlog Inicial de Producto para LTI - MVP 🎯

Se prioriza la base del ATS, la ingesta de candidatos, el *scoring* básico de IA y el flujo mínimo de colaboración.

## 1. 🧑‍🤝‍🧑 Personas (Usuarios Clave)

| Persona | Rol | Objetivos Clave |
| :--- | :--- | :--- |
| **Reclutador "Sofía"** | Talent Acquisition Specialist | Reducir el trabajo manual, gestionar alto volumen, comunicación clara y rápida. |
| **Hiring Manager "David"** | Gerente de Contratación | Evaluar candidatos de manera rápida, asegurar encaje, tomar decisiones sin reuniones. |
| **Administrador "Laura"** | Gerente de RRHH / Admin de Plataforma | Asegurar cumplimiento legal, configurar flujos, obtener reportes. |

***

## 2. Épicas y Priorización

| Épica | ID | Título | Prioridad | Justificación (PVU) | Esfuerzo Estimado (Sprints) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **E1** | Core ATS y Onboarding | Funcionalidad base del ATS. Base de operaciones (Multi-tenant, Usuarios, Ofertas). | **P1 (Must Have)** | Habilita el uso del sistema. | 2 |
| **E2** | Screening Básico Asistido por IA | Implementa la PVU clave: *Scoring* inicial de IA y filtros para la *shortlist*. | **P2 (High)** | Valida el apoyo de IA y la eficiencia. | 3 |
| **E3** | Colaboración y Feedback Mínimo | Implementa el PVU de colaboración en tiempo real y flujo de feedback estructurado. | **P2 (High)** | Valida la colaboración y la toma de decisiones sin reunión. | 2 |
| **E4** | Automatización de Entrevistas | Implementa una automatización clave (scheduling) para eficiencia. | **P3 (Medium)** | Reduce el *time-to-hire* (métrica clave). | 1 |

***

## 3. Historias de Usuario Detalladas (Backlog)

Las estimaciones de esfuerzo se basan en un sistema de Tallas (S: Pequeño, M: Mediano, L: Grande), representando la complejidad y el tiempo, y se deben completar idealmente en un sprint (10 días laborales).

### Épica 1: Core ATS y Onboarding (P1)

| ID | Título (Formato Estándar) | Talla |
| :--- | :--- | :--- |
| **HU-1.1** | Como **Administrador Laura**, quiero **configurar mi empresa (multi-tenant)** para **aislar mis datos y comenzar a operar**. | M |
| **HU-1.2** | Como **Administrador Laura**, quiero **crear y gestionar usuarios (reclutadores y managers)** para **asignar roles y permisos de acceso**. | M |
| **HU-1.3** | Como **Reclutador Sofía**, quiero **crear una Oferta de Trabajo** para **comenzar el proceso de contratación y recibir candidatos**. | M |
| **HU-1.4** | Como **Reclutador Sofía**, quiero **subir o ingresar un candidato (perfil + CV)** para **tenerlo en el sistema y comenzar el screening**. | M |

### Épica 2: Screening Básico Asistido por IA (P2)

| ID | Título (Formato Estándar) | Talla |
| :--- | :--- | :--- |
| **HU-2.1** | Como **Reclutador Sofía**, quiero **ver un "Score Inicial" de IA en la lista de candidatos de una Oferta** para **priorizar rápidamente mi revisión**. | L |
| **HU-2.2** | Como **Reclutador Sofía**, quiero **aplicar filtros a mi lista de candidatos por estado (etapa), score IA y etiquetas (tags)** para **reducir mi shortlist de manera eficiente**. | M |

### Épica 3: Colaboración y Feedback Mínimo (P2)

| ID | Título (Formato Estándar) | Talla |
| :--- | :--- | :--- |
| **HU-3.1** | Como **Reclutador Sofía**, quiero **enviar una tarjeta de candidato a David y Entrevistadores** para **solicitar su feedback formalmente**. | M |
| **HU-3.2** | Como **Hiring Manager David**, quiero **completar un formulario de feedback estructurado (scores 0-10 y Recomendación)** para **proporcionar mi evaluación de manera rápida y comparable**. | L |
| **HU-3.3** | Como **Reclutador Sofía**, quiero **ver el resultado consolidado del feedback (scores agregados y discrepancias)** para **saber inmediatamente si avanzar o requerir una reunión**. | L |

### Épica 4: Automatización de Entrevistas (P3)

| ID | Título (Formato Estándar) | Talla |
| :--- | :--- | :--- |
| **HU-4.1** | Como **Reclutador Sofía**, quiero **solicitar un enlace de auto-programación para una entrevista (Entrevistador + Candidato)** para **evitar el intercambio manual de correos para agendar**. | L |

***

## 4. Criterios de Aceptación (Ejemplos Selectos)

| ID | HU | Criterios de Aceptación |
| :--- | :--- | :--- |
| **HU-1.4** | Subir o ingresar un candidato. | **Dado que** estoy en una Oferta de Trabajo, **cuando** subo un CV, **entonces** se crea un registro en `Candidato` y `Aplicacion` (estado: Nuevo) y el CV se guarda en S3 (`file_storage`). |
| **HU-2.1** | Ver un "Score Inicial" de IA. | **Dado que** un CV ha sido procesado, **cuando** el `AI Service` calcula el score (flujo 5.1), **entonces** el campo `scoreIA` se actualiza y la lista de candidatos se ordena por este score por defecto. |
| **HU-3.2** | Completar un formulario de feedback. | **Dado que** recibí una notificación (HU-3.1), **cuando** ingreso scores (Técnico, Cultural) y una recomendación (Avanzar/Rechazar), **entonces** se crea un registro de `Comentario` con `tipo='Feedback'` y los scores se normalizan. |
| **HU-3.3** | Ver el resultado consolidado. | **Dado que** todos los miembros del panel han enviado su feedback, **cuando** reviso la tarjeta del candidato, **entonces** veo la mediana de los scores y un aviso visual de **"Discrepancia Alta"** si la desviación estándar entre scores es > 2. |

# Análisis Comparativo y Recomendación de Backlog para el MVP de LTI

Basado en el Product Requirements Document (PRD) de LTI, cuyo objetivo es validar la **Propuesta de Valor Única (PVU): "ATS colaborativo con IA contextual"**, se analizan tres enfoques de Backlog.

## 1. Tres Enfoques de Backlog

Se comparan el enfoque inicial y dos alternativas, cada una priorizando un pilar estratégico diferente.

| Enfoque | Foco de Priorización | PVU que Valida Principalmente | Épicas Clave (MVP) |
| :--- | :--- | :--- | :--- |
| **Backlog Inicial** | **Balance (IA + Colaboración)** | IA Scoring y Feedback Estructurado. | Core ATS, Screening Básico con IA, Colaboración Mínima, Programación Automática. |
| **Alternativa A** | **Eficiencia y Cumplimiento (Eje HR)** | Automatización End-to-End y Auditoría. | Core ATS, Automatización de Oferta/Cierre, Auditoría, Feedback Básico (Texto). |
| **Alternativa B** | **Colaboración y Experiencia (Eje Manager)** | Dashboard en Tiempo Real e IA Contextual Avanzada. | Core ATS, Colaboración en Tiempo Real, IA Dual (Téc/Cult) y Detección de Discrepancias. |

***

## 2. Análisis Comparativo Detallado

| Característica | Backlog Inicial (Sugerido) | Alternativa A (Eficiencia/HR) | Alternativa B (Colaboración/Manager) |
| :--- | :--- | :--- | :--- |
| **Foco de Valor** | Balanceado (IA y Colaboración mínima). | Flujo *End-to-End* y Mitigación de Riesgos (HR). | Calidad del *Screening* y Experiencia de Evaluación. |
| **IA Contextual (PVU)** | Básico (Score Único) + Filtros. | Mínimo (Keywords o Score Único Simple). | **Fuerte** (Score Dual: Téc./Cult. + Detección de Discrepancias). |
| **Colaboración (PVU)** | Fuerte (Feedback Estructurado y Consolidación). | Débil (Feedback como campo de texto simple). | **Fuerte** (Dashboard en tiempo real, Comentarios, Notificaciones). |
| **Time-to-Hire** | Medio (Mejora con filtros y feedback rápido). | **Máximo impacto** (Automatización de *Scheduling* y Oferta). | Bajo (Se enfoca en la *calidad*, no en la velocidad de la fase de evaluación). |
| **Riesgo Principal** | Riesgo de **no terminar la IA avanzada** o la colaboración en el MVP. | Riesgo de **no validar la PVU de IA diferenciadora**. Puede parecer un ATS tradicional. | Riesgo de **ignorar procesos clave** (oferta, *onboarding*) y la auditoría. |
| **Adecuación al Cliente** | **Alta.** Ideal para validar el mercado. | Media/Baja. Mejor para empresas muy reguladas. | **Alta.** Ideal para el segmento **Tech Startups/Scaleups**. |

***

## 3. Conclusión y Recomendación

El objetivo del MVP de LTI es validar la **diferenciación** que le da su PVU.

### Recomendación

Se recomienda **proceder con el Backlog Inicial sugerido** (presentado en el análisis previo).

### Justificación

El **Backlog Inicial** ofrece el mejor equilibrio para un MVP, ya que es el único que **garantiza tocar y validar mínimamente los dos pilares estratégicos diferenciadores** antes de un lanzamiento completo:

1.  **Valida la IA:** Con el *Scoring Inicial* (HU-2.1).
2.  **Valida la Colaboración:** Con el *Panel de Feedback Estructurado* y la Consolidación (HU-3.2, HU-3.3).
3.  **Aporta Eficiencia:** Con la automatización clave del *Scheduling* (HU-4.1).

Este enfoque minimiza el riesgo de construir un producto que no valide su propuesta de valor central. La **Alternativa B** es un excelente plan para la Fase 2, una vez validada la base del producto.

# 📋 Planificación Detallada del Sprint 1: Core ATS y Onboarding

Este documento detalla la planificación de las Historias de Usuario (HU) de la Épica 1 para el primer sprint (10 días laborales) del MVP de LTI. Se utiliza la metodología **Planning Poker** (escala de Fibonacci) para la estimación en Puntos de Historia (PH) y se definen los Criterios de Aceptación (CdA) para el "Definition of Done".

**Objetivo del Sprint:** Habilitar la infraestructura básica para el funcionamiento del sistema: registro de empresas (multi-tenant), gestión de usuarios y la creación de ofertas de trabajo.

## 1. Historias de Usuario del Sprint 1

| ID | Título de la Historia de Usuario | Talla Inicial (Referencia) | Puntos de Historia (PH) |
| :--- | :--- | :--- | :--- |
| **HU-1.1** | Como **Administrador Laura**, quiero **configurar mi empresa (multi-tenant)** para **aislar mis datos y comenzar a operar**. | M | **5** |
| **HU-1.2** | Como **Administrador Laura**, quiero **crear y gestionar usuarios (reclutadores y managers)** para **asignar roles y permisos de acceso**. | M | **8** |
| **HU-1.3** | Como **Reclutador Sofía**, quiero **crear una Oferta de Trabajo** para **comenzar el proceso de contratación y recibir candidatos**. | M | **5** |
| **Total Estimado del Sprint** | | | **18 PH** |

---

## 2. Tickets de Trabajo Técnicos y Criterios de Aceptación

A continuación, se desglosan los tickets de trabajo por Historia de Usuario, incluyendo la estimación en horas de trabajo y los criterios que deben cumplirse para dar por finalizada la funcionalidad.

### 2.1. HU-1.1: Configuración de Empresa (Multi-tenant)

**PH Estimación:** 5 puntos

| Ticket de Trabajo | Descripción Técnica | Servicio Afectado | Estimación (Horas) | Criterio de Aceptación (DoD) |
| :--- | :--- | :--- | :--- | :--- |
| **T1.1.1** | Diseño y Script de Migración Inicial para las tablas `Empresa` y `Usuario` (primer registro). | Auth Service/DB | 4 | **CdA 1.1.3 (Persistencia):** Los datos de la empresa y el administrador son inyectados y persisten correctamente en la DB. |
| **T1.1.2** | Implementar la lógica de *middleware* o *guard* en el **API Gateway** y el **Auth Service** para validar el `tenantId` en cada *request* REST. | API Gateway/Auth Service | 8 | **CdA 1.1.2 (Aislamiento):** Las solicitudes sin `tenantId` válido son rechazadas, y las solicitudes válidas solo acceden a datos del `tenantId` correspondiente. |
| **T1.1.3** | Implementar *endpoint* POST `/companies` para el registro inicial de la empresa con el administrador *owner*. | Auth Service | 4 | **CdA 1.1.1 (Registro):** El *endpoint* recibe los datos, crea la `Empresa` y asigna el rol `Administrador` al usuario solicitante. |
| **T1.1.4** | Construir la interfaz de usuario (UI) para el formulario de *onboarding* inicial de la empresa y la redirección al *Dashboard*. | Cliente Web (SPA) | 8 | **CdA 1.1.4 (UX):** La interfaz permite el ingreso de datos, y tras la creación exitosa, redirige al usuario al Dashboard. |

### 2.2. HU-1.2: Creación y Gestión de Usuarios

**PH Estimación:** 8 puntos

| Ticket de Trabajo | Descripción Técnica | Servicio Afectado | Estimación (Horas) | Criterio de Aceptación (DoD) |
| :--- | :--- | :--- | :--- | :--- |
| **T1.2.1** | Implementar *endpoints* CRUD (`GET`, `POST`, `PUT`, `DELETE`) para la tabla `Usuario` (`/users`) con validación de rol. | Auth Service | 8 | **CdA 1.2.1 (Creación):** El *endpoint* POST crea un usuario con el rol y `empresaId` correctos. |
| **T1.2.2** | Implementar la lógica de envío de correo de bienvenida y reseteo de contraseña inicial al crear un nuevo usuario. | Notification Service | 8 | **CdA 1.2.3 (Notificación):** El sistema dispara un correo electrónico al email del nuevo usuario inmediatamente después de la creación. |
| **T1.2.3** | Crear y configurar la tabla de *roles* y permisos básicos. Definir los roles iniciales: `Admin`, `Reclutador`, `HM`. | Auth Service/DB | 4 | **CdA 1.2.2 (Rol y Permisos):** Solo los usuarios con rol `Admin` pueden acceder a la gestión de usuarios, y el *tenantId* se aplica a la lista de usuarios recuperada. |
| **T1.2.4** | Construir la interfaz de usuario (UI) de la tabla de usuarios y el formulario de creación/edición. | Cliente Web (SPA) | 8 | **CdA 1.2.4 (Visualización):** La UI muestra la lista de usuarios activos de la empresa, y el formulario permite asignar roles predefinidos. |

### 2.3. HU-1.3: Creación de Ofertas de Trabajo

**PH Estimación:** 5 puntos

| Ticket de Trabajo | Descripción Técnica | Servicio Afectado | Estimación (Horas) | Criterio de Aceptación (DoD) |
| :--- | :--- | :--- | :--- | :--- |
| **T1.3.1** | Diseño y Script de Migración para las tablas `OfertaTrabajo` y `EquipoContratacion` con sus respectivas *foreign keys* a `Empresa`. | Job Service/DB | 4 | **CdA 1.3.3 (Persistencia):** Las tablas `OfertaTrabajo` y `EquipoContratacion` se crean en la DB del Job Service con los índices y relaciones necesarios. |
| **T1.3.2** | Implementar *endpoints* CRUD (`GET`, `POST`) para `OfertaTrabajo` (`/jobs`). Se requiere validación de *tenantId* y rol `Reclutador`. | Job Service | 8 | **CdA 1.3.1 (Creación):** El *endpoint* POST crea la Oferta solo si el usuario es `Reclutador` o `Admin` y le asigna el estado `Abierta` por defecto. |
| **T1.3.3** | Implementar un *endpoint* simple para listar los `EquipoContratacion` (requerido para asociar la Oferta a un equipo). | Job Service | 4 | **CdA 1.3.2 (Asociación):** El *endpoint* devuelve la lista de equipos activos, y al crear la oferta, esta se asocia correctamente al `equipoId` seleccionado. |
| **T1.3.4** | Construir la interfaz de usuario (UI) para el formulario de creación de Oferta de Trabajo. | Cliente Web (SPA) | 8 | **CdA 1.3.4 (Visualización):** La UI permite la creación de una nueva oferta, muestra un mensaje de éxito al completar el flujo y redirige al listado de ofertas. |

---

## 3. Resumen de Carga de Trabajo

| Categoría | Puntos de Historia (PH) | Horas Estimadas (Referencial) |
| :--- | :--- | :--- |
| **HU-1.1** (Multi-tenant) | 5 | 24 horas |
| **HU-1.2** (Gestión de Usuarios) | 8 | 28 horas |
| **HU-1.3** (Creación de Ofertas) | 5 | 24 horas |
| **Total del Sprint** | **18 PH** | **76 horas** |

Este plan de sprint es el punto de partida técnico que habilita el resto de las funcionalidades de Colaboración e IA.