# Lab 3.1: Hardening de VMs (Trusted Launch & JIT)

**Objetivo del Laboratorio:** Proteger infraestructura IaaS contra ataques de nivel de arranque y ocultar puertos de administración.

### Red Team Perspective (El vector de ataque)
Las herramientas de escaneo buscan puertos 3389 (RDP) o 22 (SSH) expuestos a Internet para realizar fuerza bruta. Además, inyectar un bootkit a nivel de sistema operativo proporciona persistencia que los antivirus convencionales no pueden detectar.

### Blue Team Mission (Tu tarea)
Endurece una Máquina Virtual desde la base hasta la red.
1. Despliega una Azure VM configurando el tipo de seguridad como Trusted Launch (habilita Secure Boot y vTPM).
2. Desde Microsoft Defender for Cloud, localiza la máquina y habilita Just-In-Time (JIT) VM access.
3. Configura JIT para que el puerto de administración solo se abra un máximo de 2 horas tras la aprobación manual.
4. Prueba: Intenta conectarte por RDP/SSH a la IP pública (el tráfico debe ser descartado). Solicita acceso JIT desde el portal y comprueba que la conexión ahora es posible.