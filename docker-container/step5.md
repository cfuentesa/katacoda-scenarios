## Creaci&oacute;n de im&aacute;gen

Vamos a crear una nueva im&aacute;gen a partir de otra. Veremos dos formas para hacer esto; **Commit** y **Dockerfile**.

###Commit

El comando **commit** nos permite crear una nueva im&aacute;gen a partir de un contenedor. Primero obtenemos la im&aacute;gen httpd:

`docker pull httpd`{{execute}}

Necesitamos crear el contenedor. Este contenedor lo usaremos como plantilla para la nueva im&aacute;gen:

`docker run -d --name httpd httpd`{{execute}}

Entramos a la consola del contenedor:

`docker exec -it httpd /bin/bash`{{execute}}

Modificamos la p&aacute;gina **index.html**

`echo "Hola Cristian Fuentes A" > htdocs/index.html`{{execute}}

`exit`{{execute}}

Para ver los cambios realizados usamos el comando **diff**:

`docker diff httpd`{{execute}}

Los estados presentados por el comando **diff** son:

| Simbolo | Descripci&oacute;n |
| ------ | ------ |
| **A** | Archivo o directorio agregado |
| **D** | Archivo o directorio eliminado |
| **C** | Archivo o directorio modificado |

Para crear la nueva im&aacute;gen a partir del contenedor:

`docker commit httpd custom_httpd`{{execute}}

Verificamos la nueva im&aacute;gen:

`docker images`{{execute}}

Por &uacute;ltimo, ejecutamos nuestra im&aacute;gen:

`docker run -d --name custom_httpd -p 8080:80 custom_httpd`{{execute}}

`curl localhost:8080`{{execute}}

## Dockerfile

Dockerfile es un archivo de texto que contiene una serie de comandos que instruyen los pasos necesarios para crear la im&aacute;gen. En este caso no es necesario un contenedor de plantilla.
Creamos nuestro archivo:

`cat <<EOT >> Dockerfile`{{execute}}
`FROM httpd`{{execute}}
`RUN echo "Hola nuevamente" > /usr/local/apache2/htdocs/index.html`{{execute}}
`EOT`{{execute}}

Para crear la nueva im&aacute;gen, usamos el comando **build**:

`docker build -t custom_httpd2`{{execute}}

Ejecute la nueva im&aacute;gen y pruebe con el comando **curl**.