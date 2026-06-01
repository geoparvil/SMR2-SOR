# Actividades de aplicación
## 2.21
Modifica los colores de la consola de PowerShell, el título de la ventana y el prompt. Añade los cambios al fichero del perfil de usuariox

<img width="471" height="355" alt="image" src="https://github.com/user-attachments/assets/1adf9642-cf88-4a41-8043-f08e2f9be9e0" />

## 2.22

Instala sobre el software de virtualización que estés usando, y donde tengas instalado el servidor, una máquina virtual donde se instale el
sistema operativo Windows 10. Llama a esa máquina virtual Cliente1. Crear máquina nueva → Windows 10. 

Nombre: Cliente1. Asignar: 2 GB RAM minimo 1 vCPU 50 GB de disco Montar ISO de Windows 10 Instalar sistema.
```mermaid
flowchart TD
    A[Abrimos VirtualBox]
    B[Ponemos nuestro nombre]
    C[Insertamos el SO]
    D[seleccionamos 2 GB RAM]
    E[Seleccionamos 1 vCPU]
    F[Seleccionamos 50 GB de espacio]
    G[Terminar]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

# 2.23
Comprueba la conexión entre las máquinas Cliente1 y Servidor utilizando el comando ping y Test-NetConnection. Ponemos ipconfig para
saber la IP y luego hacemos ping para comprobar conectividad
<img width="500" alt="image" src="https://github.com/user-attachments/assets/8870de3b-2066-478b-8734-559160962186" />
<img width="400" alt="image" src="https://github.com/user-attachments/assets/89379b53-8926-439b-bcb1-172811ccc364" />
<img width="400" alt="image" src="https://github.com/user-attachments/assets/561e3a7d-7401-4d18-b584-82d95c38ac25" />

# 2.24
Crea un usuario local llamado usuariolocal. Haz que sea un usuario estándar y créale una contraseña que él no pueda cambiar. Entra como
usuariolocal e intenta cambiarla. 





