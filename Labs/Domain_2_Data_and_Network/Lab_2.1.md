# Lab 2.1: Storage & Azure SQL Security

**Objetivo del Laboratorio:** Asegurar los datos en reposo y habilitar la detección de amenazas.

### Red Team Perspective (El vector de ataque)
La exfiltración de datos masiva ocurre habitualmente a través de cuentas de almacenamiento mal configuradas con acceso público anónimo o mediante inyecciones SQL que logran volcar bases de datos completas.

### Blue Team Mission (Tu tarea)
Cierra el acceso perimetral de los datos e implementa monitorización de amenazas.
1. Crea un Storage Account y deshabilita la opción "Allow Blob public access".
2. Opcional: Genera una clave gestionada por el cliente (CMK) en Key Vault y úsala para cifrar la cuenta de almacenamiento.
3. Crea un servidor Azure SQL y una base de datos de prueba.
4. Habilita Microsoft Defender for SQL a nivel de servidor.
5. Configura la auditoría para enviar los registros de la base de datos a un Log Analytics Workspace.
6. Prueba: Revisa el panel de Defender for Cloud en busca de recomendaciones de seguridad para los recursos que acabas de crear.