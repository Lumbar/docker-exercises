Indica la diferencia entre el uso de la instrucción CMD y ENV (Dockerfile).

--------------------------------------------------------------------------------------------------------------------------------------------

La instrucción ENV setea un valor a una variable de entorno y puede haber varias instrucciones ENV en un archivo Dockerfile mientras que la instrucción CMD 
establece el comando y/o los parámetros predeterminados a la instrucción ENTRYPOINT, que se pueden sobrescribir desde la línea de comando cuando se ejecuta el docker container y solo 
puede haber una instrucción CMD en un archivo Dockerfile (Si hay más instrucciones CMD ejecutará la última) a diferencia que ENV. Además el propósito principal de CMD es proporcionar 
valores predeterminados para un contenedor en ejecución.

El uso de ENV sería el siguiente:
ENV MY_NAME="John Doe"
En donde la variable MY_NAME se seteará con el valor "John Doe"

En cambio si se hace
CMD [ "John Doe", "$MY_NAME" ]
Esta no hará la sustitución y no hará nada.