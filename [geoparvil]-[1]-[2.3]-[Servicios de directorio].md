# Instalación y configuración de un servicio de directorio LDAP

## Instalación del servidor OpenLDAP

En esta actividad instalaremos y configuraremos un servicio de directorio utilizando OpenLDAP, 
que es una de las soluciones de software libre mas utilizadas para la gestión de directorios de linux,
Para esto usaremos un servidor ubuntu donde instalaremos el software y realizaremos su configuración.
antes debemos actualizar nuestro servidor con:

```bash
sudo apt update
```
```bash
sudo apt upgrade
```

## Instalación de los paquetes necesarios

En primer lugar, se instalan los paquetes proporcionados por el proyecto OpenLDAP. Para ello, se ejecuta el siguiente comando en el
terminal:

```bash
sudo apt install slapd ldap-utils
```
(foto)
Durante el proceso de instalación, el sistema solicita la contraseña del administrador LDAP, la cual se utilizará posteriormente para
gestionar el directorio.

Una vez finalizada la instalación, es necesario realizar su configuración inicial.


## Configuración básica del servidor LDAP

Para configurar el servidor OpenLDAP se utiliza el asistente de configuración incluido en el paquete slapd. Este asistente permite
definir los parámetros básicos del directorio.
El comando utilizado es el siguiente:

```bash
sudo dpkg-reconfigure slapd
```
Durante el proceso de configuración, el asistente va solicitando diferentes datos que se introducen de la siguiente forma: Nos pedira si
queremos omitir y le daremos a: No

(FOTO)

-Nombre del dominio DNS: prova-ioc.cat

(FOTO)

-Nombre de la organización: prova-ioc
(foto)

-Contraseña del administrador: servidor

(FOTO)

-Eliminar la base de datos cuando se purgue el paquete: No
(foto)

-Mover la base de datos antigua: Yes
(foto)

Una vez finalizado el asistente, el servidor LDAP queda correctamente configurado y listo para su uso, con una base de datos asociada
al dominio prova-ioc.cat.

# Gestión del servicio OpenLDAP

### Crear el archivo grups.ldif
#### Crear el archivo:

```text
nano grups.ldif

```

FOTO

## Conclusión

Aquí escribes qué hiciste y qué aprendiste en la práctica.
