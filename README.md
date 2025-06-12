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

# Azure Resource Manager CheatSheet

**Azure Resource Manager (ARM)** es un servicio que permite **gestionar** recursos de Azure.

Es una capa de gestión que permite:
- Crear, actualizar y eliminar recursos
- Aplicar características de gestión como: control de acceso, locks, tags
- Escribir infraestructura como código (IaC) mediante plantillas JSON

---

## Características clave

- ARM es una capa de servicio que **abarca múltiples características y servicios**, como:
  - Subscriptions
  - Management Groups
  - Resource Groups
  - Resource Providers
  - Resource Locks
  - Azure Blueprints
  - Resource Tags
  - Access Control (IAM)
  - Role-Based Access Controls (RBAC)
  - Azure Policies
  - ARM Templates

- ARM funciona como un **gatekeeper**:
  - Todas las solicitudes pasan por ARM y este decide si se permite realizar la acción solicitada sobre un recurso.

---

## Scope

- Es una **boundary of control** para los recursos de Azure.
- Permite **gobernar** los recursos al organizarlos lógicamente y aplicar reglas.
- **Niveles jerárquicos de alcance**:
  - **Management Groups**: Agrupación lógica de múltiples suscripciones
    - **Subscriptions**: Acceso a servicios de Azure con base en facturación
      - **Resource Groups**: Agrupación lógica de recursos
        - **Resources**: Recursos individuales como máquinas virtuales

---

## Otros conceptos importantes

- Una cuenta de Azure puede tener **múltiples suscripciones** (por ejemplo: Free Trial, Pay-As-You-Go, Azure for Students)

- **Resource Providers**: Lista de servicios posibles dentro de Azure. Algunos se registran automáticamente, otros requieren registro manual.

- **Resource Tags**: Son **pares clave-valor** que se asignan a recursos de Azure para clasificarlos y organizarlos.

- **Resource Locks**:
  - Previenen modificaciones o eliminaciones accidentales.
  - Tipos:
    - **CanNotDelete (Delete)**: Se puede leer y modificar, pero no eliminar el recurso.
    - **ReadOnly (Read-only)**: Solo lectura, no se puede modificar ni eliminar.

- **Blueprints**:
  - Habilitan la **creación rápida de suscripciones gobernadas**
  - Lo que defines en un blueprint (qué **debe ser** desplegado) se compara con lo que realmente fue desplegado (**qué fue** desplegado).

---

> Azure Blueprints y ARM Templates pueden trabajar juntos para estandarizar la gobernanza y despliegue de recursos en Azure.
##  ARM Templates CheatSheet

## Infraestructura como Código (IaC)
**IaC** es el proceso de **gestionar y aprovisionar** centros de datos mediante archivos de definición legibles por máquina (como archivos JSON), en lugar de configurar hardware o herramientas interactivas manualmente.

### Tipos de IaC:
- **Declarative**: Defines exactamente lo que deseas, y obtienes eso.
- **Imperative**: Defines lo que deseas en general, y el servicio intenta adivinar lo que necesitas.

---

## ARM Templates

- Son **archivos JSON que definen recursos de Azure** que deseas aprovisionar y servicios que deseas configurar.
- Son **declarativos**: obtienes exactamente lo que defines.

---

## Estructura de un template ARM

Un template ARM contiene la siguiente estructura JSON:

- **$schema**: Describe las propiedades disponibles dentro de la plantilla.
- **contentVersion**: Versión del template. Puedes asignar cualquier valor.
- **apiProfile**: Permite evitar especificar versiones de API para cada recurso.
- **parameters**: Valores que puedes pasar al template.
- **variables**: Transforman parámetros o definen valores intermedios.
- **functions**: Funciones definidas por el usuario, disponibles dentro del template.
- **resources**: Recursos que deseas desplegar o actualizar.
  - `type`: Tipo de recurso
  - `apiVersion`: Versión de API REST para ese recurso
  - `name`: Nombre del recurso
  - `location`: Región donde se desplegará
  - `other properties`: Propiedades adicionales específicas del tipo de recurso
- **outputs**: Valores que se retornan luego del despliegue.

---

> ARM Templates son esenciales para despliegues consistentes, repetibles y automatizados en entornos Azure.

# Storage Accounts CheatSheet

## Azure tiene 5 tipos de servicios de almacenamiento:

1. **Azure Blob**  
   - Almacenamiento tipo **object store** para texto y datos binarios.
   - Escalable masivamente.
   - Compatible con Data Lake Storage Gen2 para big data analytics.

2. **Azure Files**  
   - **File shares** gestionados para implementaciones en la nube o locales.

3. **Azure Queues**  
   - **NoSQL store** para almacenamiento esquemático de datos estructurados.

4. **Azure Tables**  
   - **Messaging store** confiable entre componentes de aplicaciones.

5. **Azure Disks**  
   - Volúmenes de almacenamiento de nivel de bloque (**Block-level storage**) para VMs de Azure.

---

## Tipos de rendimiento en cuentas de almacenamiento:

- **Standard**: Almacenado en discos duros (**HDDs**).
- **Premium**: Almacenado en unidades de estado sólido (**SSDs**).
  - Desempeño varía por nivel de acceso: Hot, Cool, Archive.

---

## Azure Blob Storage admite 3 tipos de blobs:

1. **Block blobs**:  
   - Almacenan texto y datos binarios.
   - Divididos en bloques.
   - Soportan hasta ~4.75 TiB.

2. **Append blobs**:  
   - Optimizado para operaciones de anexado (append).
   - Útil para logs de VMs, etc.

3. **Page blobs**:  
   - Almacenan archivos aleatorios (hasta 8 TiB).
   - Usados como discos virtuales (VHD) para VMs.

---

## Tipos de acceso en Blob Storage (para **Standard**):

- **Hot**:  
  - Acceso frecuente.
  - Mayor costo de almacenamiento, menor costo de acceso.

- **Cool**:  
  - Acceso infrecuente (≥30 días).
  - Menor costo de almacenamiento, mayor costo de acceso.

- **Archive**:  
  - Acceso muy infrecuente (≥180 días).
  - Costo más bajo de almacenamiento, mayor costo de acceso.

---

## Tiering de almacenamiento:

- **Account-Level Tiering**:  
  - Si un blob no tiene un tier definido, hereda el de la cuenta de almacenamiento.

- **Blob-Level Tiering**:  
  - Puedes elegir el tier por blob.
  - Cambiar de tier es instantáneo excepto al salir de "archive", que puede tardar horas.

> Esto se conoce como **rehydrating** un blob.

# Storage Accounts CheatSheet (Parte 2)

## Blob Lifecycle Management
Puedes crear políticas basadas en reglas para mover datos entre niveles de almacenamiento (tiers).  
Ejemplo: Después de 30 días, mover a "cool storage".

- Cuando un blob es cargado o movido de tier, **se cobra inmediatamente** según la nueva tarifa.

---

### Al mover desde un tier **más frío**:
- Se cobra como una **write operation** hacia el tier de destino.
- Se aplican cargos de operación de escritura (por cada 10,000) y cargos por GB escritos en el tier de destino.

### Al mover desde un tier **más caliente**:
- Se cobra como una **read operation** desde el tier de origen.
- Se aplican cargos de lectura (por cada 10,000) y recuperación de datos (por GB) del tier de origen.
- También pueden aplicarse cargos por eliminación anticipada si el blob se movió fuera del tier "cool" o "archive" antes de tiempo.

---

## Eliminación anticipada en cool/archive:
- Blobs en tier **cool** (solo cuentas GPv2) tienen un periodo de retención mínimo de 30 días.
- Blobs en tier **archive** tienen un periodo mínimo de retención de **180 días** (cobro prorrateado si se eliminan antes).

---

## Múltiples formas de mover datos a Azure Blob Storage:

- **AzCopy**:  
  Herramienta de línea de comandos para Windows y Linux.

- **Azure Storage Data Movement library**:  
  Librería .NET que usa AzCopy internamente.

- **Azure Data Factory**:  
  Servicio ETL de Azure.

- **Blobfuse**:  
  Acceso al sistema de archivos virtual desde Linux.

- **Azure Data Box**:  
  Dispositivo físico para transportar grandes volúmenes de datos a Azure.

- **Azure Import/Export service**:  
  Servicio para enviar discos físicos para carga de datos en Azure.

# Storage Accounts CheatSheet (Replication Types)

Cuando creas una cuenta de almacenamiento en Azure, debes elegir un **Replication Type**  
(Importante para recuperación ante desastres y tolerancia a fallos).

---

## Primary Region Redundancy  
**(Recuperación ante desastres y fallos dentro de una misma región)**

- **Locally Redundant Storage (LRS)**  
  - Copia los datos **sincrónicamente** dentro de una única región.  
  - 💰 **Opción más barata**

- **Zone-Redundant Storage (ZRS)**  
  - Copia los datos **sincrónicamente** entre **3 Zonas de Disponibilidad (AZs)** dentro de una región.

---

## Secondary Region Redundancy  
**(Recuperación ante desastres entre regiones)**

- **Geo-Redundant Storage (GRS)**  
  - Copia los datos **sincrónicamente** en la región primaria.  
  - Copia los datos **asincrónicamente** a una región secundaria.

- **Geo-Zone-Redundant Storage (GZRS)**  
  - Copia los datos **sincrónicamente** entre **3 AZs** en una región primaria.  
  - Copia los datos **asincrónicamente** a una región secundaria.

---

## Secondary Region Redundancy with Read Access  
**(Replica con acceso de solo lectura a la región secundaria)**

- **Read-Access Geo-Redundant Storage (RA-GRS)**  
  - Copia los datos **sincrónicamente** en la región primaria.  
  - Copia los datos **asincrónicamente** en la región secundaria.  
  - ✅ Permite **lectura** desde la réplica.

- **Read-Access Geo-Zone-Redundant Storage (RA-GZRS)**  
  - Copia los datos **sincrónicamente** entre AZs de la región primaria.  
  - Copia los datos **asincrónicamente** en la región secundaria.  
  - ✅ Permite **lectura** desde la réplica.

---

> 🔁 **Síncrono** = los datos se replican inmediatamente.  
> 🕒 **Asíncrono** = puede haber un pequeño retraso en la replicación (útil en desastres mayores).
