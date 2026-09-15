# Lab 2.2: Aislamiento de Red (Private Endpoints & NSGs)

**Objetivo del Laboratorio:** Eliminar los endpoints públicos de los servicios PaaS y segmentar la red.

### Red Team Perspective (El vector de ataque)
Si una base de datos o un Key Vault responden a una IP pública, es posible lanzar ataques de fuerza bruta desde cualquier lugar. Si el servicio solo vive dentro de una red virtual privada, queda invisible para los escáneres de Internet.

### Blue Team Mission (Tu tarea)
Implementa aislamiento de red para un servicio administrado.
1. Despliega un Key Vault o un Storage Account.
2. Ve a la sección de red del recurso y deshabilita el acceso público.
3. Crea un Private Endpoint y conéctalo a una subred de una VNet existente.
4. Verifica que la integración con la zona Private DNS está correctamente configurada.
5. Crea un Network Security Group (NSG) en esa subred para bloquear explícitamente el tráfico de entrada desde Internet.
6. Prueba: Intenta acceder al Storage Account desde tu equipo local (debe fallar). Despliega una máquina virtual dentro de la VNet e intenta el acceso de nuevo (debe funcionar).