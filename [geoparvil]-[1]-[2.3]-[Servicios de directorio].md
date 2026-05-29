
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
<img width="833" height="114" alt="actualizacion" src="https://github.com/user-attachments/assets/3d45f9fa-a904-434c-aca5-cfd3bbee66f0" />

## Instalación de los paquetes necesarios

Lo primero será, instalar los paquetes que nos da  el proyecto OpenLDAP. Para eso, 
ponemos el siguiente comando en la
consola:

```bash
sudo apt install slapd ldap-utils
```
<img width="1209" height="339" alt="Instalacion de paquetes" src="https://github.com/user-attachments/assets/b6db87e0-1b39-47e4-bb5e-7fedcea4b704" />

Durante la instalación, el sistema pide  la contraseña del administrador LDAP, la que se utilizará despues para
manipular el directorio.

En el siguiente apartado continuamos con la configuracion.


## Configuración  del servidor LDAP

Para configurar el servidor OpenLDAP utilizaremos el asistente de configuración que traé incluido  el paquete slapd,
Esto permite realizar las cosas basicas de nuestro directorio, El comando que usaremos es:

```bash
sudo dpkg-reconfigure slapd
```
mientras vamos haciendo el proceso de configuración, el asistente va pedir varios datos que se deben hacer de la siguiente manera: 

<img width="971" height="280" alt="Pantalla_de_asistente_de_configuracion" src="https://github.com/user-attachments/assets/7259b1f1-d547-4c06-8c80-b031fa98aed8" />

-Nombre del dominio DNS: prova-ioc.cat

<img width="713" height="231" alt="nombre-del-dominio" src="https://github.com/user-attachments/assets/cb3867fb-16e5-4ba4-a9be-bd55f776a032" />

-Nombre de la organización: prova-ioc

<img width="725" height="204" alt="nombre-de-la-organización" src="https://github.com/user-attachments/assets/bdc180ea-4103-4127-8235-58e5a1f14ceb" />


-Contraseña del administrador en mi caso abrevie a: server

<img width="728" height="242" alt="contraseña-del-admin-ldap" src="https://github.com/user-attachments/assets/c7870836-2ee9-476e-9a42-7623d87bf167" />

-Eliminar la base de datos cuando se purgue el paquete

<img width="757" height="210" alt="configuracion-slapd" src="https://github.com/user-attachments/assets/dc82aad8-9996-4754-8a9a-6c55b64b55eb" />


-Mover la base de datos antigua: Yes

<img width="750" height="253" alt="mover-la-base-de-datos-antigua" src="https://github.com/user-attachments/assets/7e200348-1866-49b9-bbcf-2d6498b24863" />

Una vez finalizado el asistente, el servidor LDAP queda correctamente configurado y listo para su uso, con una base de datos asociada
al dominio prova-ioc.cat.

# Gestión del servicio OpenLDAP

### Crear el archivo grups.ldif
#### Para Crear el archivo usaremos:

```text
nano grups.ldif

```
El contenido de este archivo debe ser el siguiente:

<img width="1194" height="214" alt="archivo-grups contenido" src="https://github.com/user-attachments/assets/ff96b863-c964-47f2-b155-774e98ebf33e" />

Luego de esto deberemos importar el archivo al directorio esto se hace con este comando
```text
sudo ldapadd -x -D cn=admin,dc=prova-ioc,dc=cat -W -f grups.ldiff
```
<img width="836" height="112" alt="importe el archivo en el directorio" src="https://github.com/user-attachments/assets/4a325416-3c0b-42b2-bd77-1f76d016fa48" />

Ahora deberemos crear el archivo usuaris.ldif

## crear el archivo usuaris-ldif
### Para crear este archivo usamos:
```text
nano usuaris.ldif
```
Y debera contener lo sigiente:
```text
dn: cn=Queralt Serra,cn=smx,ou=alumnat,dc=IOC-domini,dc=cat
cn: Queralt Serra
sn: Serra
uid: queralt
uidNumber: 1100
gidNumber: 1001
homeDirectory: /home/queralt
loginShell: /bin/bash
objectClass: inetOrgPerson
objectClass: organizationalPerson
objectClass: person
objectClass: posixAccount
objectClass: top
```
debe verse así
<img width="664" height="230" alt="usuaris ldif" src="https://github.com/user-attachments/assets/82572d72-5ff9-4378-b0c0-520fcf1eb95a" />

### ahora importamos el usuario con:
```text
sudo ldapadd -x -D cn=admin,dc=prova-ioc,dc=cat -W -f usuaris.ldif
```
### Ahora estableceremos contraseña con ldappasswd
Para añadir contraseña al al LDIF debemos usar este comando:

```text
sudo ldappasswd -S -W -D "cn=admin,dc=prova-ioc,dc=cat" -x "cn=Queralt Serra,cn=smx,ou=alumnat,dc=prova-ioc,dc=cat"
```
<img width="1282" height="78" alt="cambio-de-contraseña-ldappasswd" src="https://github.com/user-attachments/assets/c3c246ce-63ba-45fc-8a4d-bb5924054106" />

##lo siguiente sera mostrar el arbol LDAP 
eso se hace con este comando:
```text
sudo ldapsearch -x -LLL ldap:/// -b dc=prova-ioc,dc=cat dn
```

<img width="896" height="406" alt="Muesta-organizativa" src="https://github.com/user-attachments/assets/1fdc834c-681b-40ba-8bcd-56fe6e390575" />

Y para la unidad organizativa seria este:
```text
sudo ldapsearch -x -H ldap:/// -b ou=alumnat,dc=prova-ioc,dc=cat dn
```
<img width="857" height="175" alt="muestra-de-arbol-ldap" src="https://github.com/user-attachments/assets/2a174611-bba6-4cb6-9a3d-9556045306c9" />

## Para mostrar un usuario concreto Hacemos lo siguiente:
```text
sudo ldapsearch -x -H ldap:/// -b "cn=Queralt Serra,cn=smx,ou=alumnat,dc=prova-ioc,dc=cat"
```
Ademas de con comandos los directorios pueden configurarse con interfaz grafica las herramientas mas recomendadas son:
```text
LDAP Account Manager (LAM)
```
```text
Apache Directory Studio
```
```text
phpLDAPadmin
```
Con esto podemos realizar todas configuraciones que hacemos desde la terminal, realizaremos la instalaciones de una interfaz grafica.

# Instalacion de una interfaz grafica para gestionar un directorio
Para que sea mas facil manipular el servicio de directorio vamos a instalar un interfaz grafica llamada phpLDAPadmin, 
Que permite manipular el directorio desde la web.

#### Para instalar usamos este comando:
```text
sudo apt install phpldapadmin
```
<img width="959" height="369" alt="instalacion-php-ldap" src="https://github.com/user-attachments/assets/1779953c-2ddc-4899-b213-2acca7c6d5a8" />

Ahora debemos configurarlo.

# Configuracion phpLDAPadmin
Entraremos al archivo de configuración que debemos modificar, para entrar directamente y modificarlo se  usa el siguiente comando:
```text
sudo nano /usr/share/phpldapadmin/config/config.php
```
Deberemos entrar y cambiar el nombre del dominio por prova-ioc y los demas que mencionen ioc-domini,
debe quedar como la imagen:

<img width="878" height="653" alt="Captura de pantalla 2026-05-29 112337" src="https://github.com/user-attachments/assets/8ff84335-98eb-442e-a1c7-2ada6b7ed09d" />

una vez listo salimos y continuamos. 

# Conexion con el servidor LDAP
debemos revisar que tenemos apache con 
```text
sudo systemctl status apache2
```
si no deberemos intalarlo con: 
```text
sudo apt install apache 2 
```
En mi caso si lo tengo así que vamos a verificar nuestra ip con:

```text
ip a
```
<img width="875" height="279" alt="Captura de pantalla 2026-05-29 112827" src="https://github.com/user-attachments/assets/9e8846b0-ae1f-4f09-a04f-9bb20f925008" />

una vez la tengamos debemos escribir lo siguiente para entrar al servidor:
```text
http://(192.168.1.35)/phpldapadmin
```
esto en mi caso deberan sustituir (192.168.1.35) por la ip de su servidor

#### una  vez dentro se debera ver de esta manera:
<img width="1919" height="1026" alt="Captura de pantalla 2026-05-29 113707" src="https://github.com/user-attachments/assets/11b7c0df-e3a1-40f4-84a3-904bab86d7fc" />

podemos acceder con las credenciales que de admin que utilizamos.

# Conclusion
En esta práctica realizamos la instalación y configuracion de un servidor de directorio openLDAP, asi como la instalacion de una interfaz grafica para que sea simple manipularlo sin una consola.


