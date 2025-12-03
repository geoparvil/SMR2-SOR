# Monitor de recursos
El objetivo de esta actividad es que trabajes con el Monitor de Recursos. Abra el Monitor de recursos y analice el uso del procesador, la RAM, el disco duro y la red. Todo ello en tiempo real y con gráficos que te ayudan a evaluar el estado actual del sistema.

```mermaid
flowchart TD
    A[Inicio] --> B[Abrir Administrador de tareas]
    B --> C[Hacer clic en redimiento]
    C --> D[Hacer clic arriba a la derecha en Monitor de recursos ]
    D --> E[Navegar por las pestañas para analizar CPU RAM disco duro y red]
    E --> F[Hacer clic derecho en un registro y seleccionar Propiedades]
    F --> G[Fin]
```
<img width="1918" height="1028" alt="MONITOR_recursos" src="https://github.com/user-attachments/assets/8504a3be-6539-4ed0-be86-3c5b0681a24c" />
Deberia verse así, las propiedades no pueden verse en windows server 2019.

# Rendimiento del equipo
El objetivo de esta actividad es permitirte estudiar el desempeño de tu equipo y comprobar si funciona de la forma más adecuada.
Abra el monitor de rendimiento y agregue un contador sobre el uso del disco duro: lectura y escritura. Además, configúrelo para analizarlo durante 15 minutos.

```mermaid
flowchart TD
    A[Inicio] --> B[Buscar en la barra perfmon]
    B --> C[En la ventana ir a Monitor de rendimiento]
    C --> D[Hacer clic en el nombre Monitor de rendimiento en el panel izquierdo]
    D --> E[Hacer clic en el boton verde de anadir contadores]
    E --> F[En la lista elegir Disco fisico]
    F --> G[Seleccionar contadores lectura y escritura y pulsar Aceptar]
    G --> H[Crear conjunto de recopiladores de datos manual damos click derecho y nuevo]
    H --> I[Abrir propiedades y fijar duracion en 15 minutos]
    I --> J[CIniciar el conjunto de recopiladores]
    J --> K[Fin]
```
<img width="1002" height="710" alt="Monitor_rendimiento" src="https://github.com/user-attachments/assets/2b13e5be-bce5-485c-92a5-8c6e1517c376" />
Deberia verse así
