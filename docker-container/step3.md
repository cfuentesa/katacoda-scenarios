## Variables de ambiente

Podemos definir variables de ambiente al momento de ejecutar nuestro contenedor. Usamos **-e VARIABLE=VALOR**.
Usaremos la imagen mariadb, la cual es la versi&oacute;n open source de MySQL. Obtenemos la im&aacute;gen:

`docker pull mariadb`{{execute}}

Tratemos de ejecutar la im&aacue;gen:

`docker run mariadb`{{execute}}

Como podemos ver, la ejecuci&oacute;n falla, ya que la im&aacute;gen requiere de ciertas variables de ambiente:

| Variable | Descripción |
| ------ | ------ |
| MYSQL_ROOT_PASSWORD | Esta variable es obligatoria y especifica la password del superusuario |
| MYSQL_DATABASE | Variable opcional y especifica el nombre de la base qie se desea crear |
| MYSQL_USER y MYSQL_PASSWORD | Estas variables son opcionales y especifican al superusuario de la base creada en la variable anterior. |

Ejecutamos la im&aacute;gen especificando las variables de ambientes necesarias:

`docker run -d --name mariadb -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=example -e MYSQL_USER=example_user -e MYSQL_PASSWORD=password mariadb`{{execute}}

Ahora el contenedor fue creado exitosamente. Ingresamos a la consola del contenedor:

`docker exec -it mariadb /bin/bash`{{execute}}

Verificamos ejecutando en comando mysql y verificando la BD y el usuario creado:

`mysql -uroot -p`

Para ver las bases de datos ejecutamos:

`show databases;`

Para ver los usuarios:

`SELECT User FROM mysql.user;`
