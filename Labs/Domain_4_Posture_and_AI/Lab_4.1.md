# Lab 4.1: Defender CSPM y Attack Path Analysis

**Objetivo del Laboratorio:** Evaluar la postura de seguridad global y priorizar remediaciones basadas en el contexto del ataque.

### Red Team Perspective (El vector de ataque)
Un atacante no explota vulnerabilidades al azar, sino que busca el camino más corto hacia datos críticos. Si una VM expuesta a Internet tiene una vulnerabilidad y, al mismo tiempo, una identidad con permisos sobre un almacén de claves, ese es el vector principal.

### Blue Team Mission (Tu tarea)
Utiliza la inteligencia de Defender para identificar rutas de ataque explotables antes de que lo haga el atacante.
1. Accede a Microsoft Defender for Cloud y asegúrate de tener el plan Defender CSPM habilitado.
2. Dirígete a la sección Attack Path Analysis.
3. Analiza las rutas de ataque generadas que muestran la combinación de exposición en red, vulnerabilidades y permisos excesivos.
4. Utiliza el Cloud Security Explorer para construir una consulta personalizada buscando máquinas virtuales expuestas a Internet con vulnerabilidades críticas.