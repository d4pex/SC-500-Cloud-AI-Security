La metáfora clave de este capítulo: RBAC es el sistema de tarjetas de acceso (quién puede abrir qué puerta), y Azure Policy es el inspector del edificio (que comprueba que todo cumple la normativa, sin importar quién haya abierto la puerta). Ambos son necesarios.

1.Azure RBAC (Role-Based Access Control) vs. Entra Roles
Esta es la trampa número uno del examen SC-500.
* Entra Roles (Ej. Global Administrator): Controlan el tenant de identidad (usuarios, grupos, políticas de acceso condicional).
* Azure RBAC Roles (Ej. Owner, Contributor, Reader): Controlan los recursos de Azure (Máquinas virtuales, Key Vaults, Storage Accounts).
* Nota Crítica: Ser "Global Administrator" en Entra ID NO te da acceso por defecto a las suscripciones de Azure. Para ello, el Global Admin debe ir al portal y activar un botón llamado "Access management for Azure resources", lo que le otorga temporalmente el rol RBAC de User Access Administrator en la raíz del tenant.

2.Management Groups (Grupos de Administración)
* Son carpetas lógicas que se sitúan por encima de las suscripciones. Se pueden anidar hasta 6 niveles.
* El superpoder: Si asignas una política o un rol RBAC a un Management Group, se aplicará automáticamente a todas las suscripciones actuales y futuras que se muevan dentro de esa carpeta.
* Tip de diseño: Nunca asignes políticas directamente en el "Tenant Root Group" a menos que sea 100% necesario que aplique literalmente a cada rincón de la empresa.

3.Azure Policy (El Inspector del Edificio)
A diferencia de RBAC (que dice "puedes o no puedes crear una VM"), Policy dice "puedes crear la VM, pero solo si tiene estas características".

Los 4 componentes de Azure Policy:
* Definition (Definición): Una regla individual (ej. "Todas las Storage Accounts deben usar HTTPS").
* Initiative (Iniciativa / Policy Set): Un paquete de varias definiciones agrupadas (ej. "Iniciativa de Seguridad ISO 27001", que contiene cientos de reglas).
* Assignment (Asignación): El acto de aplicar una Definición o Iniciativa a un Management Group, Suscripción o Resource Group.
* Exemption (Exención): Crear una exclusión temporal para un recurso específico con una justificación (ej. exención aprobada por el CISO por 90 días).

4.Los Efectos de las Políticas (Policy Effects)
Cuando un recurso choca contra una política, ocurre un "Efecto". Tienes que saber diferenciar los principales:
* Deny (Denegar): Bloquea la creación del recurso directamente.
* Audit (Auditar): Deja que el usuario cree el recurso, pero lo marca como "No conforme" en el panel de control.
* Append (Anexar): Añade algo antes de crearlo (ej. forzar que se añadan ciertas etiquetas de facturación).
* Modify (Modificar): Corrige configuraciones (ej. activar HTTPS forzado si el usuario se olvidó).
* DeployIfNotExists (DINE): Si la política detecta que falta algo (ej. el agente de Defender for Servers no está en una VM), usa una Managed Identity para instalarlo automáticamente. Es el efecto más poderoso y automatizado.

5.Regulatory Compliance Dashboard (Panel de Cumplimiento Normativo)
* Ubicado dentro de Microsoft Defender for Cloud.
* Microsoft ya ha creado iniciativas preconfiguradas para los estándares de la industria más comunes (ISO 27001, NIST, PCI-DSS, CIS).
* No tienes que crear reglas desde cero. Simplemente vas al dashboard, asignas la iniciativa PCI-DSS a tu suscripción, y el sistema mapeará todos tus recursos contra los requisitos legales, dándote un informe de qué arreglar para pasar una auditoría.