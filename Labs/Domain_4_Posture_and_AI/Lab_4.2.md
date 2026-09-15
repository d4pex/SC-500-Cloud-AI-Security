# Lab 4.2: Microsoft Sentinel (SIEM & SOAR)

**Objetivo del Laboratorio:** Centralizar telemetría, cazar amenazas mediante KQL y automatizar la respuesta a incidentes.

### Red Team Perspective (El vector de ataque)
Durante una infiltración, el atacante intenta evadir la monitorización o esconderse en el ruido legítimo de la red. Si los equipos defensivos no correlacionan logs de múltiples sistemas, los movimientos tácticos pasan desapercibidos.

### Blue Team Mission (Tu tarea)
Levanta los ojos de la red y configura un SIEM funcional.
1. Crea un Log Analytics Workspace y habilita Microsoft Sentinel en él.
2. Conecta un Data Connector básico (como Azure Activity) para ingerir eventos de la infraestructura.
3. Crea una regla analítica personalizada utilizando KQL que dispare una alerta si alguien elimina un Grupo de Seguridad de Red (NSG).
4. Crea una automatización (Logic App) que envíe una notificación por correo electrónico cuando se genere esta alerta.
5. Prueba: Elimina un NSG de prueba en tu suscripción y comprueba cómo Sentinel genera un incidente y dispara la automatización.