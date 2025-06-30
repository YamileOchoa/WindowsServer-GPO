# 🖥️ Implementación de Active Directory con Directivas de Grupo (GPO)

## 📋 Descripción  
Esta implementación configura un entorno empresarial utilizando **Windows Server**, donde se centraliza la gestión de usuarios, equipos y configuraciones mediante **Active Directory (AD)** y **Directivas de Grupo (GPO)**. Este enfoque mejora la seguridad, eficiencia y estandarización de políticas en redes corporativas.

---

## ✨ Características

- Creación de un dominio empresarial (ej. `empresa.local`)  
- Registro y administración de usuarios y grupos desde el servidor  
- Unión de equipos cliente al dominio  
- Aplicación de políticas de grupo (GPO) como:
  - Bloqueo del Panel de Control  
  - Establecer fondo de pantalla institucional  
  - Restricción de instalación de programas  
- Administración centralizada y segura de configuraciones  

---

## 🛠️ Requisitos

- Windows Server 2019 o superior  
- Máquina cliente con Windows 10 o 11  
- Software de virtualización (VMware Workstation o VirtualBox)  
- Red interna configurada entre servidor y cliente  
- Privilegios de administrador en ambas máquinas  

---

## ⚙️ Pasos de Implementación

### 1️⃣ Instalación de Active Directory en el Servidor
1. Abrir **Server Manager**  
2. Seleccionar **Manage > Add Roles and Features**  
3. Activar el rol **Active Directory Domain Services (AD DS)**  
4. Finalizar la instalación y seleccionar **Promote this server to a domain controller**  
5. Crear un nuevo bosque y asignar el nombre del dominio: `empresa.local`  
6. Configurar la contraseña para el modo de restauración (DSRM)  
7. Completar la promoción y reiniciar el servidor

---

### 2️⃣ Creación de Usuarios y Grupos
1. Abrir **Active Directory Users and Computers**  
2. Crear una **OU (Organizational Unit)**, por ejemplo `UsuariosEmpresa`  
3. Crear un nuevo usuario dentro de la OU (ej. `cnavarro`)  
4. Crear grupos si es necesario (ej. `Contabilidad`, `TI`)  
5. Asignar usuarios a los grupos correspondientes

---

### 3️⃣ Unión de un Cliente al Dominio
1. En el cliente, configurar el mismo adaptador de red virtual que el servidor  
2. Cambiar el nombre del equipo si se desea (ej. `PC-CARLA`)  
3. Ir a **Sistema > Cambiar configuración > Cambiar dominio**  
4. Especificar el dominio `empresa.local`  
5. Ingresar credenciales de administrador del dominio  
6. Reiniciar el cliente  
7. Iniciar sesión como usuario del dominio

---

### 4️⃣ Configuración de una GPO
1. Abrir **Group Policy Management** en el servidor  
2. Crear una nueva GPO (ej. `RestriccionesUsuarios`)  
3. Editar la GPO con las siguientes configuraciones:  
   - `User Configuration > Administrative Templates > Control Panel`  
     - Activar: *Prohibit access to Control Panel*  
   - `User Configuration > Desktop > Desktop Wallpaper`  
     - Establecer una imagen institucional como fondo  
   - `User Configuration > System > Prevent access to registry editing tools`  
     - Activar para bloquear cambios avanzados  
4. Vincular la GPO a la OU `UsuariosEmpresa`

---

### 5️⃣ Verificación de Aplicación de Políticas
1. Iniciar sesión con un usuario del dominio en el cliente  
2. Comprobar que las políticas configuradas (fondo, restricciones) se apliquen  
3. Validar la aplicación de GPOs con el comando `gpresult /r` o con `rsop.msc`

---

## 📚 Conceptos Aplicados

- Servicios de Dominio de Active Directory (AD DS)  
- Unidades Organizativas (OU)  
- Gestión de usuarios y grupos  
- Group Policy Objects (GPO)  
- Unión de clientes al dominio  
- Configuración y seguridad en red empresarial  

---

## ✅ Resultados Esperados

- Administración centralizada de usuarios y equipos  
- Aplicación automática de configuraciones de seguridad  
- Reducción de errores y configuraciones manuales  
- Estandarización de políticas a nivel organizacional  

---

## 💡 Beneficios Empresariales

- Control y seguridad desde un único servidor  
- Menor carga operativa para TI  
- Configuración homogénea en todos los equipos  
- Escalabilidad para múltiples departamentos o sedes  
- Mayor cumplimiento normativo y trazabilidad
