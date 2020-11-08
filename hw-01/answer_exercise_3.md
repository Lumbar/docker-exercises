Crea un contenedor con las siguientes especificaciones:
a. Utilizar la imagen base NGINX haciendo uso de la versión 1.19.3
b. Al acceder a la URL localhost:8080/index.html aparecerá el mensaje
HOMEWORK 1
c. Persistir el fichero index.html en un volumen llamado static_content

• ¿Qué comandos has utilizado?

--------------------------------------------------------------------------------------------------------------------------------------------

Los comandos que se utilizaron fueron:

docker pull nginx:1.19.3

docker volume create --name static_content --opt type=none --opt device=D:\docker-data\homework1 --opt o=bind

docker run -ti -v static_content:/usr/share/nginx/html -p 8080:80 nginx:1.19.3
