Los comandos que se utilizaron fueron:

docker build -t go-healthcheck:v1 .

docker run -ti -p 8080:80 go-healthcheck:v1

docker ps -a