## Almacenamiento

Cuando eliminamos un contenedor, todos los datos asociados a dicho contenedor se pierden. A esto se refiere con arquitectura Stateless. Podemos cambiar este comportamiento y mantener todos los datos usando un almacenamiento persistente.
Para habilitar un almacenamiento persistente usamos la opci&oacute;n **-v**, el cual enlaza el sistema de archivos del contenedor con el sistema de archivos del Host u otro sistema persistente.
Primero removemos todos los contenedores creados previamente:

`docker rm -f $(docker ps -aq)`{{execute}}

Primero preparemos el directorio de almacenamiento. Debemos dar permisos de lectura/escritura. La aplicaci&oacute;n MariDB se ejecuta con un usuario UID 999.
Ejecute los siguientes comandos para preparar el directorio de almacenamiento:

`mkdir /mnt/data`{{execute}}

`chown 999:999 /mnt/data`{{execute}}

El siguiente paso es crear el contenedor de mariadb indicando el uso del directorio de almacenamiento para los datos de la BD:

`docker run -d -v /mnt/data:/var/lib/mysql --name mariadb -e MYSQL_ROOT_PASSWORD=password mariadb`{{execute}}

Cree una nueva base de datos. Primero entrar a la consola del contenedor:

`docker exec -it mariadb /bin/bash`{{execute}}

Entramos al utilitario mysql:

`mysql -u root -p`

Creamos la nueva base de datos:

`create database persistent;`

Validamos la nueva base de datos:

`show databases;`

Salga del utilitario y de la shell con el comando exit.
Revisamos los archivos creados en nuestro directorio host:

`ls -l /mnt/data/`{{execute}}

Ahora elimine el contenedor:

`docker rm -f mariadb`{{execute}}

Verifique que a&uacute;n estan los archivos creados por el contenedor:

`ls -l /mnt/data/`{{execute}}

Vuelva a crear el contenedor y verifique que la base de datos persistent a&uacute;n existe.

Por &uacute;ltimo, elimine todos los contenedores:

`docker rm -f $(docker ps -aq)`{{execute}}
