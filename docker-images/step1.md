## Administrar Im&aacute;genes

Para buscar una im&aacute;gen en el repositorio p&uacute;blico https://hub.docker.com usamos el comando **docker search**. Por ejemplo, si queremos buscar la im&aacute;gen httpd, usamos el siguiente comando:

`docker search httpd`{{execute}}

Una vez que hemos encontrado la im&aacute;gen, podemos traerla hasta nuestro servidor Docker usando el comando **docker pull**:

`docker pull httpd`{{execute}}

Para obtener una lista de im&aacute;genes disponibles en nuestro servidor Docker:

`docker images`{{execute}}

Podemos ver en la lista que aparece la im&aacute;gen httpd con TAG **latest**. Cuando no especificamos el TAG, por defecto, obtendr&aacute; **latest**. Si queremos obtener un TAG en espec&iacute;fico:

`docker pull httpd:2.4.39`{{execute}}

Obtenemos nuevamente la lista de im&aacute;genes disponibles y encontramos la nueva im&aacute;gen disponible.

`docker images`{{execute}}

Para eliminar una im&aacute;gen del servidor, usamos el comando **docker rmi**:

`docker rmi httpd:2.4.39`{{execute}}

Volvemos a obtener la lista y veremos que ya no existe.

`docker images`{{execute}}
