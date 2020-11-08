Indica la diferencia entre el uso de la instrucción ADD y COPY (Dockerfile).

--------------------------------------------------------------------------------------------------------------------------------------------

Ambas instrucciones siguen la misma forma básica y logran prácticamente lo mismo:
ADD <src>... <dest>
COPY <src>... <dest>

Aunque la instrucción ADD y COPY pueden realizar la misma tarea, la diferencia está en que la instrucción COPY no admite una URL como 
argumento <src>, por lo que no se puede usar para descargar archivos desde ubicaciones remotas, todo lo que se desea copiar debe estar en
el contexto de compilación local. Además la instrucción COPY no da ningún tratamiento especial a los archivos, ya que si se copia un 
archivo de almacenamiento, este file aterrizará en el contenedor exactamente como es sin ningún intento de desempaquetarlo.