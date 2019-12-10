## Detener e iniciar un contenedor

Podemos detener e iniciar un contenedor con los comandos **docker stop** y **docker start**. Para detenerl el contenedor:

`docker stop [ID_CONTENEDOR]`

Reemplace [ID_CONTENEDOR] por el Id del contenedor. Para iniciar el contenedor:

`docker start [ID_CONTENEDOR]`

Para remover un contenedor usamos el comando **docker rm**. Si el contenedor esta en ejecuci&oacute;n debemos agregar la opci&oacute;n -f:

`docker rm -f [ID_CONTENEDOR]`

Para poder acceder a los servicios que entrega el contenedor. podemos mapear los puertos del contenedor con los puertos del servidor Docker, para tal efecto usamos la opci&oacute;n -p. Ahora lo ejecutamos mapeando el puerto 80 del contenedor con el puerto 8080 del servidor Docker:

`docker run -d -p 8080:80 httpd`{{execute}}

Validamos el servicio http del contenedor con:

`curl localhost:8080`{{execute}}

Mientras el contenedor est&aacute; en ejecuci&oacute;n, podemos inspeccionar sus par&aacute;metrosusando **docker inspect**.

`docker inspect [ID_CONTENEDOR]`
