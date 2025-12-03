# Creación de un nuevo bosque
Esta práctica consiste en crear un bosque en un sistema Microsoft Windows Server 2019 recién instalado. Indique todos los pasos que debe seguir para abrir el asistente para crear un nuevo dominio.
```mermaid
flowchart TD
    A[Inicio] --> B[Hacer clic en Hogar]
    B --> C[Hacer clic en Administrador del servidor]
    C --> D[Hacer clic en Gestionar > Agregar roles y funciones]
    D --> E[El asistente inicia y continuar hasta Roles del servidor]
    E --> F[Marcar Servicios de dominio de Active Directory]
    F --> G[Cargar caracteristica e instalar]
    G --> H[Hacer clic en Promocione este servidor al controlador de dominio]
    H --> I[Fin]
```
<img width="1028" height="764" alt="image" src="https://github.com/user-attachments/assets/8f037063-2f38-472b-87f0-53941e586daa" />

Aqui ya estaria instalado el servicio y creado el dominio

# Establecer pautas grupales
El propósito de esta actividad es encontrar los pasos correctos para realizar una configuración general en los usuarios del dominio, por ejemplo, que no puedan reorganizar la barra de tareas ni eliminar íconos del menú de inicio. Este tipo de directivas se aplican a todos los usuarios que forman parte del ámbito empresarial.

```mermaid
flowchart TD
    A[Inicio] --> B[Abrir Administracion de directivas de grupo]
    B --> C[Abrir Bosque > Dominios > tu dominio]
    C --> D[Entrar a Objetos de directiva de grupo]
    D --> E[Click derecho en Politica de dominio predeterminada y Editar]
    E --> F[Ir a Configuracion de usuario > Directivas > Plantillas administrativas]
    F --> G[Abrir Menu Inicio y barra de tareas]
    G --> H[Habilitar Evitar que los usuarios modifiquen la barra de tareas]
    H --> I[Habilitar Impedir cambios en el menu Inicio]
    I --> J[Cerrar editor y aplicar ]
    J --> K[Fin]
```
<img width="1036" height="776" alt="image" src="https://github.com/user-attachments/assets/9112ae58-b9a2-4ce9-9076-85275d3d1e44" />
Esto es lo que debemos hacer 
