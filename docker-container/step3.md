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

Ahora el contenedor fue creado exitosamente. Verificamos ejecutando en comando mysql y verificando el usuario creado:

`docker exec -it mariadb mysql -uexample_user -ppassword example -e "show databases;"`{{execute}}

