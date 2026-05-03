# Sistema de Banca por Internet BP - Arquitectura de Solución

Este repositorio contiene la documentación técnica y de arquitectura para el nuevo **Sistema de Banca por Internet del Banco BP**. La solución está diseñada para ofrecer una experiencia omnicanal moderna, segura y de alta disponibilidad, integrando sistemas legacy con tecnologías cloud nativas.

## 1. Contexto del Negocio

### Problema que se busca resolver
Modernizar los canales digitales de BP para superar las limitaciones de lentitud y disponibilidad de los sistemas antiguos. El sistema debe consolidar información de la **Plataforma Core** y el **Sistema de Información Complementaria**, garantizando el cumplimiento normativo de notificaciones.

### Objetivos del Negocio
* **Omnicanalidad:** Aplicaciones Web (SPA) y Móviles (Multiplataforma) consistentes.
* **Disponibilidad 24/7:** Aislamiento de caídas de sistemas legacy mediante patrones de resiliencia.
* **Cumplimiento Normativo:** Sistema de notificaciones por al menos dos canales para cada movimiento.
* **Seguridad:** Onboarding digital con biometría y autenticación bajo estándar **OAuth 2.0**.

## 2. Stakeholders

| Stakeholder | Interés Principal |
| :--- | :--- |
| **Clientes de BP** | Acceso rápido, seguro y gestión integral de su salud financiera. |
| **Auditores de Seguridad** | Validación de estándares OAuth 2.0 y robustez del onboarding facial. |
| **Administradores del Banco** | Estabilidad operativa e integración exitosa de los sistemas internos. |

## 3. Arquitectura de la Solución

### Componentes Principales
* **Frontend:** Angular (Web SPA) y Flutter (App Móvil).
* **Backend:** Microservicios en AWS.
* **Seguridad:** Flujo OAuth 2.0 e integración con AWS Rekognition para biometría.
* **Integración:** Capa de Adaptadores para conectar con el Core Bancario y Sistemas Complementarios.
* **Resiliencia:** Implementación de **Circuit Breaker** y **Caché (Redis)** para mitigar la latencia del Core Legacy.

## 4. Decisiones de Arquitectura (ADR)

| Decisión | Justificación |
| :--- | :--- |
| **Microservicios** | Escalabilidad independiente y segmentación de responsabilidades. |
| **Patrón Saga** | Consistencia de datos distribuidos en transacciones financieras. |
| **Flutter** | Desarrollo costo-eficiente con un único codebase para iOS y Android. |
| **OAuth 2.0** | Estándar de la industria para autorización segura en clientes públicos. |

## 5. Riesgos y Mitigación
* **Riesgo:** Lentitud extrema del Core Bancario. -> **Mitigación:** Estrategia Cache-Aside y Circuit Breakers.
* **Riesgo:** Fallos en servicio de terceros (Rekognition). -> **Mitigación:** Proceso de contingencia o validación asíncrona.

---
*Documento de Arquitectura de Solución - Bryan Pomaquero*
