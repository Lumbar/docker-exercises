# Docker Exercises

MDAS - Principios y herramientas de desarrollo

# hw-01

- Para el ejercicio 3 se crea un archivo index.html con el contenido HOMEWORK 1 y se copia este archivo a la carpeta creada para el volumen en la siguiente ruta D:\docker-data\homework1.
  Luego se prueba el correcto funcionamiento ingresando a la siguiente url http://localhost:8080/index.html.
  Para este ejercicio no fue necesario usar un Dockerfile.

- Para el ejercicio 4 se creó un Dockerfile y se probó la URL http://localhost/index.html y el resultado fue un estado "healthy" pero si se cambia la url a http://localhost:8081/index.html dará un estado unhealthy.

- Para el ejercicio 5 se creó un archivo docker-compose.yml, luego se creó el network y se compiló este archivo y al final se probó la url http://localhost:5601/ y se siguieron las instrucciones para el uso de la página.