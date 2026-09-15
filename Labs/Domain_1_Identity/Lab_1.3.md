# Lab 1.3: Azure Key Vault & Managed Identities

**Objetivo del Laboratorio:** Eliminar credenciales embebidas en código y asegurar el almacén de secretos.

### Red Team Perspective (El vector de ataque)
Buscar en repositorios de código o scripts de automatización en busca de cadenas de conexión y secretos en texto plano es una de las fases de enumeración más rentables para un atacante.

### Blue Team Mission (Tu tarea)
Despliega un almacén seguro e implementa acceso sin contraseñas estáticas.
1. Despliega un Azure Key Vault configurado con Azure RBAC para el plano de datos.
2. Desactiva el acceso desde redes públicas en las opciones de red del Key Vault.
3. Habilita una Managed Identity (System-assigned) en una máquina virtual de Azure.
4. Concede permisos a esa Managed Identity para leer secretos del Key Vault.
5. Prueba: Conéctate a la máquina virtual e interactúa con el Key Vault mediante la CLI utilizando únicamente la identidad de la máquina.