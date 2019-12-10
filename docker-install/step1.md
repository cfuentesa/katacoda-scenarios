## Instalaci&oacute;n de Docker CE

Para el sistema operativo Centos 7, Docker CE est&aacute; disponible en los repositorios estandares de yum. Para instalar Docker ejecute el siguiente comando:

`yum install docker -y`{{execute}}

Una vez finalizada la instalaci&oacute;n, podemos iniciar el servicio Docker de la siguiente manera:

`systemctl start docker`{{execute}}

Para que el servicio quede habilitado de manera autom&aacute;tica:

`systemctl enable docker`{{execute}}

