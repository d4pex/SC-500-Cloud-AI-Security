Si las Storage Accounts son la caja fuerte, Defender for Storage es el detector de metales y las cámaras de seguridad. No bloquea el ataque de entrada, pero te avisa al instante de que algo va mal.

1.¿Qué es Defender for Storage (v2)?
Es un plan de protección específico dentro de Microsoft Defender for Cloud. Realiza tres trabajos principales:
* Monitoreo de Actividad: Analiza patrones anómalos. Ej. Un usuario que normalmente descarga 10 archivos de repente descarga 1.000 a las 3:00 AM.
* Escaneo de Malware (Malware Scanning): Escanea cada blob que se sube con el motor de Defender Antivirus antes de que otra aplicación lo lea.
* Detección de amenazas en datos sensibles: Integrado con Microsoft Purview, sabe si el blob atacado contenía simples facturas o números de tarjetas de crédito (elevando la severidad de la alerta).
* Tip de Examen: Si una pregunta menciona que se cobra por "transacción" o que no incluye escaneo de malware, está hablando de la versión antigua (v1). La respuesta siempre será migrar a v2.

2.Modelos de Habilitación (Enablement Models)
Este es el clásico escenario trampa de examen:
* Per Subscription (Por Suscripción): LA FORMA RECOMENDADA. Si lo activas aquí, cada nueva Storage Account que crees en el futuro quedará protegida automáticamente el día 1.
* Per Storage Account (Por cuenta): Lo activas cuenta a cuenta. Es peligroso porque si alguien crea una cuenta nueva, nacerá sin protección hasta que alguien se acuerde de activarla manualmente.

3.El Escaneo de Malware (Malware Scanning on Upload)
Tienes que entender cómo funciona el flujo porque no es mágico, tiene límites:
* No bloquea en tiempo real (Not real-time block): El archivo se sube y luego se escanea. Un archivo infectado existe brevemente en tu cuenta. Defender evalúa y le añade una "Etiqueta" (Index Tag) diciendo si está limpio o infectado. Tus aplicaciones deben estar programadas para leer esa etiqueta antes de usar el archivo.
* Limitaciones:
	* No puede escanear archivos de más de 2 GB.
	* Si el usuario sube el archivo ya cifrado (ej. un zip con contraseña), Defender no puede escanearlo (Saldrá como Scan not supported).
* Facturación (Cuidado en el examen): El escaneo de malware se cobra por Gigabyte escaneado, no por archivo ni por cuenta. Existe un límite mensual (cap) configurable. Si lo superas, los archivos dejarán de escanearse silenciosamente.

4.Integración con Purview (Sensitive Data Threat Detection)
* Defender, por sí solo, no sabe qué hay dentro de los blobs.
* Purview escanea y etiqueta los datos (ej. "Contiene datos bancarios").
* Cuando los dos se comunican, si alguien hace una descarga masiva anómala, Defender preguntará a Purview qué etiquetas tenían esos archivos. Si contenían datos bancarios, la alerta subirá automáticamente a High Severity.

5.Flujo de Respuesta a Incidentes (El patrón clásico)
En los casos de estudio (Case studies), te preguntarán en qué orden responder a un incidente de almacenamiento. El patrón correcto es:
* Identificar/Contener: Deshabilitar la credencial (ej. el SAS o el Service Principal) que está haciendo el ataque.
* Investigar: Abrir el incidente en Microsoft Sentinel para ver el timeline.
* Erradicar: Rotar las claves compartidas si estuvieron expuestas.
* Ajustar (Supression): Si la alerta resultó ser un falso positivo (ej. un nuevo proceso de backup interno), puedes crear una "Suppression rule" (Regla de supresión) para que Sentinel no genere más alertas molestas sobre ese proceso específico.