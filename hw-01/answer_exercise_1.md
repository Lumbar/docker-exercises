Indica la diferencia entre el uso de la instrucción CMD y ENTRYPOINT (Dockerfile).

--------------------------------------------------------------------------------------------------------------------------------------------

El propósito principal de la instrucción CMD es proporcionar ejecutables y argumentos predeterminados para un contenedor en ejecución, que pueden ser sobrescritos, mientras que la instrucción ENTRYPOINT 
proporciona ejecutables y argumentos específicos, para restringir el uso de la imagen.

La instrucción ENTRYPOINT luce similar a la instrucción CMD, porque también permite especificar un comando con parámetros. La diferencia es que el comando ENTRYPOINT y parámetros no se ignoran cuando el 
contenedor Docker se ejecuta con parámetros de línea de comando.

Presentaciones de ambas instrucciones de la manera que son similares:

Exec form: 
CMD [“executable”, “arg1”, “arg2”]
ENTRYPOINT [“executable”, “arg1”, “arg2”]

Shell form:
CMD executable arg1 arg2
ENTRYPOINT executable arg1 arg2


Un ejemplo sería la siguiente:

Si se tiene el siguiente Dockerfile:

---------------------------------------------------------------------------------------------
FROM debian:jessie-slim

RUN apt-get update                                      && \
    apt-get install -y --no-install-recommends             \
        cowsay                                             \
        screenfetch                                     && \
    rm -rf /var/lib/apt/lists/*

ENV PATH "$PATH:/usr/games"
CMD ["cowsay", "Yo, CMD !!"]
---------------------------------------------------------------------------------------------

Se buildea la imagen:

docker build -t demo .

Y se ejecuta el contenedor:
docker run demo

Aparecerá algo como:

---------------------------------------------------------------------------------------------
Yo, CMD !!
---------------------------------------------------------------------------------------------

Y si se ejecuta lo siguiente:
docker run demo screenfetch -E

Se sobrescribirá la salida y aparecerá otra cosa totalmente diferente al output anterior.

En cambio con ENTRYPOINT si se tiene el anterior dockerfile pero con ENTRYPOINT

---------------------------------------------------------------------------------------------
FROM debian:jessie-slim

RUN apt-get update                                      && \
    apt-get install -y --no-install-recommends          \
        cowsay                                          \
        screenfetch                             &&      \
    rm -rf /var/lib/apt/lists/*

ENV PATH "$PATH:/usr/games"

ENTRYPOINT ["cowsay", "Yo, Entrypoint!!"]
---------------------------------------------------------------------------------------------

Y se ejecuta el contenedor:
docker run demo

Aparecerá algo como:

---------------------------------------------------------------------------------------------
Yo, Entrypoint!!
---------------------------------------------------------------------------------------------

Y si se ejecuta lo siguiente:
docker run demo screenfetch -E

Aparecerá algo como:

---------------------------------------------------------------------------------------------
Yo, Entrypoint!! screenfetch -E
---------------------------------------------------------------------------------------------

Como era de esperar, los argumentos pasados en el comando docker run se agregan al ejecutable y el argumento, establecido en la instrucción entryPoint.


