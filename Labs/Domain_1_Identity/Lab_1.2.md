# Lab 1.2: Privileged Identity Management (PIM)

**Objetivo del Laboratorio:** Eliminar los permisos de administrador permanentes (Standing Access) e implementar acceso Just-In-Time.

### Red Team Perspective (El vector de ataque)
Si comprometo una cuenta de un administrador que tiene el rol asignado de forma ininterrumpida (24/7), tengo control total inmediato. No tengo que esperar a que el administrador realice ninguna acción para heredar sus privilegios.

### Blue Team Mission (Tu tarea)
Reduce la superficie de ataque exigiendo que los administradores eleven sus privilegios solo cuando los necesitan.
1. Accede a Privileged Identity Management (PIM) en el portal de Azure.
2. Busca el rol de Security Administrator o Global Administrator.
3. Quita las asignaciones Active y convierte a tus usuarios de prueba en Eligible.
4. Configura los ajustes del rol: requiere justificación en texto, aprobación de un tercero y una duración máxima de 4 horas.
5. Prueba: Inicia sesión con el usuario de prueba e intenta acceder a un recurso denegado. Luego, ve a PIM, activa el rol y verifica que ahora sí tienes acceso.