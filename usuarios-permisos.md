# Gestionar Permisos de Ficheros o Directorios en Linux  a Nivel Usuario

#### Introducción

**Unix** es un Sistema Operativo **Multiusuario**.

![Varios][1]

**GNU/Linux** está basado en el sistema Unix (al igual que MAC).

¿Que es **Multiusuario**?

Primero:

* Un **usuario** dispone de una cuenta de *usuario* que se compone de nombre de **usuario (login)** y de **contraseña (password)**.
* Las cuentas de *usuario* son creadas por el **administrador**.
* Los *usuarios* deberán pertenecer al menos a un **grupo**.

Tipos de usuarios:

* usuario **root** (El todo poderoso)
	* Administrador del sitema
	* Acceso total a todos los archivos y directorios
	* Controla la administración de cuentas de usuarios
	* Tiene privilegios sobre todo el sistema 
	* Modifica, instala, detiene, reconfigura procesos del sistema.
* Usuarios **especiales**
	*  bin, daemon, adm, lp, sync, shutdown, mail, operator, squid, apache, etc.
	* Se les llama también cuentas del sistema
	* Asumen distintos privilegios de root dependiendio de la cuenta.
	* No tienen contraseñas.
	* Se les conoce como cuentas de "no inicio de sesión" (nologin).
	* Se crean (generalmente) automáticamente al momento de la instalación de Linux o de la aplicación.
* Usuarios **normales**
	* Se usan para usuarios individuales.
	* Cada usuario dispone de un directorio de trabajo, ubicado generalmente en /home.
	* Cada usuario puede personalizar su entorno de trabajo.
	* Tienen solo privilegios completos en su directorio de trabajo o HOME.

Un Sistema **Multiusuario** permite que dos o más usuarios utilicen sus programas.

#### Permisos

A todo fichero o directorio en un sistema Linux se le asocian permisos en tres aspectos:

| Permiso | Descripcion | simbolo |
| :------: | :-------: | :------: |
| lectura | Accede al contenido para poder ver el contenido | r |
| Escritura | Modifica el Contenido del fichero | w |
| Ejecución | Ejecuta una aplicación, programa o script | x |

Los *permisos* o *derechos* que los usuarios pueden tener sobre determinados ficheros, se establecen en tres niveles.

* Permisos del propietario (Comúnmente llamado **"usuario"**).
* Permisos del **"grupo"**.
* Permisos del resto de usuarios (o también llamados **“otros”**).

Estos privilegios se establecen para todos los directorios del sistema incluyendo el **HOME** de cada *usuario*.

#### Permisos de Usuario
* El propietario es aquel *usuario* que genera o crea un fichero/carpeta dentro de su directorio de trabajo (**HOME**).
* Cada *usuario* puede crear los ficheros que quiera dentro de su *directorio de trabajo*.
* En principio, **él y solamente él** será el que tenga acceso a la información contenida en los ficheros y directorios que hay en su directorio *HOME*.
#### Permisos de Grupo
* Por default cada *usuario* pertenece a un *grupo de trabajo*. 
* Cuando se gestiona un **grupo** se gestionan todos los *usuarios* que pertenecen a éste. 

#### Permisos de Otros

* los *usuarios* que no pertenecen al *grupo* de trabajo, pero que pertenecen a **otros grupos de trabajo**, se les denomina **resto de usuarios (Otros)** del sistema.

### Comandos utiles

#### ¿Cómo puedo ver en qué usuario estoy?

Comando **whoami** .- Es el comando utilizado para mostrar el nombre de *usuario* actual.
> $ whoami
> 
> paul

Comando **users** .- Es el comando utilizado para mostrar los nombres de *usuario* **conectados** a la computadora actual.
> $ users
> 
> alexis johan paul

#### ¿Cómo puedo ver a qué grupo pertenesco?

Comando **groups** .- Muestra los grupos a los que pertenece el *usuario* actual.

> $ groups paul 
> 
> paul : paul profesores uami proyecto

#### ¿Cómo sé qué permisos tienen mis ficheros o directorios?

Comando **ls -l** .- El Comando **ls** Muestra el listado del directorio actual; si le añadimos la opcion **-l** nos permite listar la información de permisos, usuario, grupo, tamaño, fecha de modificaión entre otras caracteristicas más, del directorio actual.

> ls -l 
> 
![ls][3]

Analicemos este ejemplo: 

![ls-secciones][4]

Observemos la Mascara(Permisos) 

![permisos][5]

| Tipo de Archivo | Significado |
| :----: | :----: |
| - | Archivo común * |
| d | Directorio * |
| l | Enlace |
| s | Socket |
| p | Pipe |
| c | Caracter Especial |
| b | bloque |

¿Como modifico **permisos** a los ficheros de determinado directorio/carpeta?

![Duda][2]

Comanado **chmod** .- Es el comando que cambia los permisos de los ficheros y directorios.

Hay 2 cosas importantes que tener en cuenta

|Simbolo de Pertenencia |
|----- | 
| Usuario (u) proviene de user | 
| Grupo (g) proviene de group |
| Otros (o) proviene de other |

| Orden |
| ------- |
| + añade |
|  - quita |
| = asigna(reescribe) |

Sintaxis de ejecucion del comando 

| Comando | pertenecia-orden-permiso | fichero/directorio |
|-----|-----|
| chmod | **ug+rw** | reporte.doc |

#### Ejemplos

> chmod **uo-x** mi-imagen.jpg
> 
> chmod **u=rwx,o=r** prueba.c
> 
> chmod **u=rx,g+w,o-r** application.py
> 
> chmod **u=rwx,go=rx** Compartir/

[1]: Imagenes/ok.png
[2]: Imagenes/duda.png
[3]: Imagenes/ls.jpg
[4]: Imagenes/ls-secciones.jpg 
[5]: Imagenes/permisos.jpg
