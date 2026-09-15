# Roadmap de Estudio: SC-500 (Cloud & AI Security)

La certificación **Microsoft SC-500** es densa y abarca desde el control de identidades hasta la nueva gobernanza sobre modelos de IA. Para conquistarla (especialmente si vienes de un perfil ofensivo y quieres entender cómo funcionan las defensas), te recomiendo seguir este plan de asalto en 3 fases:

## Plan de Asalto (Fases de Estudio)

### Fase 1: Reconocimiento (Teoría y Fundamentos)
*   **Guía Oficial Microsoft:** Revisa los pesos de cada dominio en la página oficial de la certificación para alinear tu esfuerzo.
*   **Apuntes del Repositorio:** Estudia los 27 capítulos de apuntes incluidos en la carpeta `/Apuntes`. Los he estructurado y filtrado para ir directamente al grano de lo que se evalúa a nivel arquitectónico y técnico, marcando las típicas trampas de configuración.

### Fase 2: Explotación y Movimiento Lateral (Laboratorios Prácticos)
La consola de Azure no se aprende leyendo. Para esta fase, debes replicar configuraciones reales en tu propio tenant. Sigue la estructura de retos de la sección **"Estructura de Laboratorios"** más abajo y ensúciate las manos desplegando las defensas desde cero.

### Fase 3: Exfiltración (Simulacros y Testing)
*   **Assessment Oficial:** Haz la evaluación de prueba gratuita de Microsoft Learn para medir tu nivel base.
*   **El Jefe Final:** Enfréntate al simulacro masivo de este repositorio (`Simulacro Completo SC-500.md`). He consolidado 86 preguntas complejas de casos de uso real, listas para que te autoevalúes con las soluciones ocultas.

---

## Estructura de Laboratorios (Hands-On)

He dividido el material práctico en 4 carpetas correspondientes a los 4 dominios del examen. A medida que avances en tus propias prácticas, ve guardando tus comandos, scripts de PowerShell/CLI y capturas de pantalla en sus respectivos directorios dentro de la carpeta `/Labs`:

### `/Labs/Domain_1_Identity`
*Prácticas de seguridad de identidad y acceso.*
*   **Lab 1.1:** Implementación de acceso condicional y políticas de riesgo (Identity Protection).
*   **Lab 1.2:** Configuración de Privileged Identity Management (PIM) para accesos JIT.
*   **Lab 1.3:** Gestión de secretos, claves y certificados con Azure Key Vault.

### `/Labs/Domain_2_Data_and_Network`
*Prácticas sobre gobernanza, bases de datos y seguridad perimetral.*
*   **Lab 2.1:** Configurar platform-level security para Azure SQL y cifrado de Storage Accounts.
*   **Lab 2.2:** Despliegue de aislamiento de red (Private Endpoints, NSGs y ASGs).
*   **Lab 2.3:** Monitorización e imposición de reglas con Azure Policy.

### `/Labs/Domain_3_Compute_and_Apps`
*Prácticas sobre máquinas virtuales, Kubernetes y servicios PaaS.*
*   **Lab 3.1:** Despliegue de Trusted Launch y Azure Disk Encryption en VMs.
*   **Lab 3.2:** Controles de seguridad en Azure Functions, App Service y Logic Apps.
*   **Lab 3.3:** Asegurar clústeres de AKS y Azure Arc-enabled servers.

### `/Labs/Domain_4_Posture_and_AI`
*Prácticas sobre XDR, SIEM y la nueva frontera de la IA.*
*   **Lab 4.1:** Gestión de postura multicloud con Microsoft Defender CSPM.
*   **Lab 4.2:** Ingesta de logs, KQL y creación de reglas analíticas/SOAR en Microsoft Sentinel.
*   **Lab 4.3:** Asegurar entornos de AI Workloads, Copilot y configurar el AI Gateway.