# Lab 2.3: Azure Policy

**Objetivo del Laboratorio:** Imponer reglas de gobierno y configuración de seguridad a nivel de suscripción.

### Red Team Perspective (El vector de ataque)
La falta de controles automatizados permite que los desarrolladores desplieguen infraestructura insegura por error (ej. puertos abiertos, falta de logs), creando oportunidades constantes para los atacantes.

### Blue Team Mission (Tu tarea)
Crea barandillas de seguridad (guardrails) automáticas.
1. Accede a Azure Policy y busca una política integrada para denegar la creación de Storage Accounts sin tráfico HTTPS.
2. Asigna la política a tu grupo de recursos de prueba.
3. Prueba: Intenta desplegar una cuenta de almacenamiento deshabilitando la transferencia segura obligatoria. La política debe bloquear la creación y mostrar el error de cumplimiento.