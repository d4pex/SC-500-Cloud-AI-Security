# Lab 1.1: Conditional Access & Identity Protection

**Objetivo del Laboratorio:** Bloquear accesos anómalos y forzar MFA utilizando políticas dinámicas basadas en riesgo.

### Red Team Perspective (El vector de ataque)
El atacante ha conseguido un volcado de credenciales en texto plano de la Dark Web e intenta acceder al portal de Azure usando una IP desde la red Tor. Si no hay MFA o detección de riesgo de sesión, el atacante entra sin hacer ruido.

### Blue Team Mission (Tu tarea)
Tu misión es configurar las defensas de Entra ID para detener este ataque automatizado.
1. Accede a Microsoft Entra ID > Security > Conditional Access.
2. Crea una política que requiera MFA obligatoria para todos los usuarios con roles de administrador.
3. Dirígete a Identity Protection y configura una "Sign-in risk policy".
4. Establece que si el riesgo de inicio de sesión es Medium o High, se requiera MFA o se bloquee el acceso directamente.
5. Prueba: Intenta iniciar sesión con un usuario de prueba usando el navegador Tor o una VPN de otro país y verifica el bloqueo.