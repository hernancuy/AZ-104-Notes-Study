# AZ-104 Azure Administrator Associate #
## Microsoft Entra ##

**Active Directory (AD)** es el servicio de **gestión de identidad y acceso** de Microsoft. Ayuda a los empleados a iniciar sesión y acceder a recursos.

**Azure Active Directory (Azure AD)** es la versión en la nube de AD de Microsoft, como un servicio de identidad (**Identity as a Service - IDaaS**).

## Ediciones de Azure Active Directory:
1. **Free**: MFA gratuito, SSO, seguridad básica y registro de usuarios, gestión de usuarios.
2. **Office 365 Apps**: Protección de datos empresariales, SLA, sincronización entre nube y local.
3. **Premium 1 (P1)**: Arquitectura híbrida, grupos dinámicos, **Acceso condicional**.
4. **Premium 2 (P2)**: Protección de identidad (P2), gobierno de identidad.

Azure AD puede **autorizar** y **autenticar** múltiples fuentes:

- A tu AD local usando **Azure AD Connect**
- A tu aplicación web vía **App Registrations**
- Permitir a los usuarios iniciar sesión con su proveedor de identidad, ej. Facebook o Google, vía **External Identities**
- A Office 365 o **Microsoft Azure**

## Terminología de Active Directory:

- **Domain**: Un dominio es un área de una red organizada por una única base de datos de autenticación.
- **Active Directory Domain**: Es una **agrupación lógica** de objetos de AD en una red.
- **Domain Controller (DC)**: Un controlador de dominio es un servidor que **autentica** identidades de usuario y **autoriza** su acceso a recursos.
- **Domain Computer**: Un equipo registrado con una base central de autenticación. Sería un objeto de AD.
- **AD Object**: Es el elemento básico de Active Directory, como: usuarios, grupos, impresoras, equipos, carpetas compartidas.
- **Group Policy Object (GPO)**: Objeto virtual con configuraciones de políticas. Controla qué objetos de AD tienen acceso a qué recursos.
- **Organizational Units (OU)**: Subdivisión dentro del AD para agrupar usuarios, grupos, equipos y otras unidades.
- **Directory Service**: Servicio como **Active Directory Domain Services (AD DS)** que almacena datos de directorio y los hace disponibles a usuarios y administradores. Este servicio se ejecuta en un Domain Controller.

## Azure Active Directory - Tenants, Services y Usuarios

Un **tenant** representa una **organización** en Azure Active Directory. Un tenant es una instancia dedicada del servicio de Azure AD. Se crea automáticamente cuando te registras en alguno de los siguientes servicios:
- Microsoft Azure
- Microsoft Intune
- Microsoft 365

Cada Azure AD tenant es distinto y separado de otros Azure AD tenants.

Cuando se realiza una migración completa de AD a Azure, **no todas las funciones de AD están soportadas**, y en ese caso se necesita usar **Azure Active Directory Domain Services (AD DS)**, que proporciona **servicios de dominio gestionados**, como:

- Unión a dominio (Domain joins)
- Políticas de grupo (Group policies)
- Protocolo de acceso a directorios ligero (LDAP)
- Autenticación Kerberos / NTLM

## Funcionalidades de Azure AD Connect:

- **Password hash synchronization**: Método de inicio de sesión que sincroniza un hash de la contraseña del AD local con Azure AD.
- **Pass-through authentication**: Método de inicio de sesión que permite usar la misma contraseña local y en la nube.
- **Federation integration**: Entorno híbrido con infraestructura de AD FS local, para renovación de certificados.
- **Synchronization**: Crea usuarios, grupos y otros objetos, asegurando coincidencias entre datos locales y en la nube.
- **Health Monitoring**: Monitoreo robusto con una ubicación central en el portal de Azure para ver esta actividad.


## Usuarios

Los usuarios representan una **identidad para una persona o empleado** en tu dominio. Un usuario tiene credenciales de inicio de sesión que puede usar para acceder al portal de Azure.

### Tipos de usuarios en Azure AD:

- **Users**: Usuarios que pertenecen a tu organización.
- **Guest Users**: Usuarios invitados que pertenecen a otra organización.

---

## Grupos

Los grupos permiten al propietario del recurso (o propietario del directorio de Azure AD) asignar un conjunto de permisos de acceso a todos los miembros del grupo, sin tener que hacerlo individualmente.

### Los grupos contienen:

- **Owners**: Tienen permisos para agregar y eliminar miembros.
- **Members**: Tienen permisos para realizar acciones.

## Asignación (Assignment)

- Puedes asignar roles directamente a un grupo.
- Puedes asignar aplicaciones directamente a un grupo.


## Request to Join Groups

El propietario del grupo puede permitir que los usuarios encuentren sus propios grupos para unirse, en lugar de asignarlos manualmente. También puede configurar el grupo para aceptar automáticamente a todos los usuarios que se unan o requerir aprobación.

### Hay **cuatro formas de asignar derechos de acceso a recursos** a los usuarios:

- **Direct assignment**: El propietario del recurso asigna directamente el usuario al recurso.
- **Group assignment**: El propietario del recurso asigna un grupo de Azure AD al recurso, lo que automáticamente otorga acceso a todos los miembros del grupo.
- **Rule-based assignment**: El propietario del recurso crea un grupo y usa una regla para definir qué usuarios están asignados a un recurso específico.
- **External authority assignment**: El acceso proviene de una fuente externa, como un directorio local o una aplicación SaaS.


## Device Management Cheat Sheet

**Device Management** permite a las organizaciones administrar laptops, desktops y teléfonos que necesitan acceso a recursos en la nube.

La gestión de dispositivos se encuentra bajo **Azure Active Directory (Azure AD)**.

### Hay 3 formas de registrar (unir) dispositivos a Device Management:

#### 1. Azure Registered
- Dispositivos o móviles **propiedad personal**
- Inician sesión con una cuenta local o personal
- Compatibilidad con Windows 10, iOS, Android y MacOS

#### 2. Azure AD Joined
- Dispositivos **propiedad de la organización**
- Inician sesión con una cuenta organizacional
- Acceso solo a dispositivos que existen **en la nube** (**Cloud Native**)
  - Windows 10, Windows Server 2019

#### 3. Hybrid Azure AD Joined
- Dispositivos **propiedad de la organización**
- Inician sesión con cuenta de servicios de dominio de Active Directory propiedad de la organización
- Acceso a dispositivos que existen en la nube o **en local** (**on-premise**)
  - Windows 7, 8.1, 10, Windows Server 2008 o posterior

---

## Mobile Device Management (MDM)
- Control total del dispositivo, permite borrar datos y restaurarlo a estado de fábrica.

## Mobile Application Management (MAM)
- Publicar, enviar, configurar, asegurar, monitorear y actualizar apps móviles para tus usuarios.

## Azure Roles Cheat Sheet

Dentro de Azure existen **3 tipos de roles**:

1. **Classic subscription administrator roles**: El sistema de roles original.
2. **Azure roles**: Conocidos como Role-Based Access Controls (RBAC), construidos sobre Azure Resource Manager.
3. **Azure Active Directory (Azure AD) roles**: Se usan para administrar recursos de Azure AD en un directorio.

## Identity Access Management (IAM)
Permite crear y asignar roles Azure (RBAC) a los usuarios.

---

## Tipos de roles

Los roles restringen el acceso a acciones sobre recursos (también llamadas operaciones). Existen **2 tipos de roles**:

1. **BuiltInRole**: Roles administrados por Microsoft; solo puedes usar los que ya existen.
2. **CustomRole**: Rol creado por ti mismo con tu propia lógica personalizada.

### Role Assignment
Se refiere al momento en que se aplica un rol a un usuario. Un role assignment está compuesto por:
- Security Principal
- Role Definition
- Scope

Azure proporciona **4 roles incorporados**:
- Owner
- Contributor
- Reader
- User Access Administrator

---

## Classic Administrators (3 tipos):

1. **Account Administrator**: Propietario de la suscripción, responsable de facturación. No tiene acceso al portal de Azure.
2. **Service Administrator**: Tiene acceso completo al portal de Azure y es asignado como Owner a nivel de suscripción.
3. **Co-Administrator**: Tiene el mismo acceso que el Owner en el nivel de suscripción.

---

## Roles importantes en Azure AD

- **Global Administrator**: Acceso total a todo.
- **User Administrator**: Acceso completo para crear y gestionar usuarios.
- **Billing Administrator**: Puede hacer compras, administrar suscripciones y tickets de soporte.

> Puedes crear roles personalizados en Azure AD, pero necesitas adquirir: **Azure AD Premium P1 o P2**.
>>>>>>> c156598e467f98309ad50ab336d05cb3ffb490bb
