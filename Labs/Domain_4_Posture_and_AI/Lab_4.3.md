# Lab 4.3: AI Workloads & Copilot Security

**Objetivo del Laboratorio:** Defender la nueva frontera tecnológica securizando modelos de Inteligencia Artificial.

### Red Team Perspective (El vector de ataque)
La inyección de prompts, los jailbreaks y el envenenamiento de los datos de contexto son las nuevas metodologías de explotación. El objetivo es manipular el comportamiento del modelo de IA para que entregue información confidencial o ejecute instrucciones maliciosas.

### Blue Team Mission (Tu tarea)
Aplica controles preventivos sobre las peticiones que recibe un modelo de lenguaje.
1. Explora el servicio Azure AI Content Safety.
2. Configura e implementa Prompt Shields para detectar y bloquear intentos de ataque de inyección directos (usuario) e indirectos (datos manipulados).
3. Investiga cómo implementar AI Gateway usando Azure API Management para auditar el uso del modelo, registrar interacciones y limitar el número de tokens por consumidor.