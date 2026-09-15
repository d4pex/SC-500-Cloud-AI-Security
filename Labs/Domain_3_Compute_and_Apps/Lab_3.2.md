# Lab 3.2: Seguridad en PaaS (App Service)

**Objetivo del Laboratorio:** Proteger aplicaciones web nativas forzando autenticación y aislando su tráfico de salida.

### Red Team Perspective (El vector de ataque)
Las aplicaciones alojadas en la nube sin mecanismos de autenticación centralizados o que comunican con bases de datos a través de Internet son blancos fáciles para la interceptación de tráfico y el acceso no autorizado.

### Blue Team Mission (Tu tarea)
Asegura el acceso de entrada y la red de salida de una aplicación web.
1. Despliega un Azure App Service web app.
2. Habilita la autenticación integrada (EasyAuth) utilizando Microsoft Entra ID como proveedor de identidad.
3. Configura la aplicación para requerir autenticación en todas las solicitudes.
4. Configura VNet Integration para que el tráfico saliente de la aplicación web fluya directamente hacia una red virtual privada.
5. Prueba: Navega a la URL de tu aplicación. Deberías ser redirigido obligatoriamente al inicio de sesión de Microsoft.