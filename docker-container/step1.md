## Ejecutar un contenedor

En este laboratorio, vamos a ejecutar un contenedor a partir de la im&aacute;gen de Apache **httpd**. Primero obtenemos la im&aacute;gen que necesitamos:

`docker pull httpd`{{execute}}

Antes de ejecutar el contenedor, vamos a revisar que contenedores est&aacute;n en ejecuci&oacute;n con el siguiente comando:

`docker ps`{{execute}}

Para ejecutar un contenedor usamos el comando **docer run**; para el caso de la im&aacute;gen httpd:

`docker run httpd`{{execute}}

Podemos ver que el terminal a quedado tomado y no podemos seguir trabajando. Para detener la  ejecución usamos la combinaci&oacute;n **(Ctrl + C)**.
Para revisar los contenedores que est&aacute;n en ejecuci&oacute;n y detenidos usamos:

`docker ps -a`{{execute}}

Para ejecutar el contenedor en background usamos la opci&oacute;n -d:

`docker run -d httpd`{{execute}}

Esto generar&aacute; un ID random, en el cu&aacute; los 12 primeros caracteres son usados como ID del contenedor.

`docker ps`{{execute}}

Para revisar el log del contenedor usamos el comando **docker logs**.

`docker logs [ID_CONTENEDOR]`{{execute}}

Reemplace [ID_CONTENEDOR] pr el Id del contenedor. Podemos ejecutar algunos comandos dentro del contenedor usando el comando **docker exec**.

`docker exec -i [ID_CONTENEDOR] ls -l`

La opci&oacute;n -i nos permite ejecutar el commando sin tener que estar en el contenedor. Para ejecutar comandos desde el interior del contenedor usamos las opcione -i -t:

`docker exec -it [ID_CONTENEDOR] /bin/bash`

