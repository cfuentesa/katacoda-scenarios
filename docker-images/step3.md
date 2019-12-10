## Etiquetar y subir Im&aacute;genes

A través de las etiquetas, podemos crear nuevas im&aacute;genes para posteriormente subirlas a nuestro repositorio.
Para asignar una nueva etiqueta a una im&aacute;gen, usamos el comando **docker tag**. Primero obtenemos la im&aaute;gen **httpd**.

`docker pull httpd`{{execute}}

Creamos una nueva im&aacute;gen llamada[usuario_docker]/httpd:latest con el siguiente comando:

`docker tag httpd:latest [usuario_docker]/httpd:latest`

Reemplace [usuario_docker] con su cuenta de Docker Hub.
Ahora podemos subir esta nueva im&aacute;gen a Docker Hub u otro repositorio con el comando **docker push**.

`docker push [usuario_docker]/httpd:latest`

Una vez subida la im&aacute;gen, podemos verla con el comando **docker search**.

`docker search [usuario_docker]/*`



