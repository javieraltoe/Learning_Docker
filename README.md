# Learning_Docker
Learning Docker with youtube and docker desktop


Link: https://www.youtube.com/watch?v=CV_Uf3Dq-EU

GITHUB: https://github.com/pablokbs/peladonerd/tree/master/docker/12/app

¿Que es Docker?

¿Para qué sirve Docker?

¿Como instalar Docker en windows/linux/Ubuntu?


¿Como generar una imagen de Docker con Dockerfile?
Comandos Docker:

Para descargar una Imagen, esto me descarga la ultima imagen que existe:
Docker pull <nombre de la imagen>

Para ejecutar un contenedor nuevo a partir de una imagen:
Docker run <nombre de la imagen>

Para ver las imagenes que tengo descargadas:
Docker images | head

Para ver los contenedores que tengo corriendo:
Docker ps

Para ver todos los contenedores que estuvieron corriendo hace un tiempo:
Docker ps -a

Para volver a correr un docker que se frenó:
Docker start <container_id>



Para ver los logs del contenedor
Docker logs <container_id> o docker logs <name>

Para ver los logs del contenedor pero se queda esperando siguiendo los logs
Docker logs -f <container_id> o docker logs -f <name>

Para ejecutar un commando dentro de un docker que ya esta corriendo:
Docker exec -it <container_id> sh
El -i va a crear una sesion interactiva
El t va a emular una terminal
De esa manera puedo ejecutar sh que es una shell donde puedo ejecutar comandos de linux por ejemplo ls para ver que tengo en el contenedor como si fuera un linux

Para detener el contenedor:
Docker stop <container_id>

Correr un contenedor en background:
Docker run -d <nombre de la imagen que quiero correr>
-d significa ditach





Como crear un Dockerfile:
Vim dockerfile


FROM node.12.22.1-alpine3.11 

WORKDIR /app
COPY . .
RUN yarn install - - production

CMD [“node”,”/app/src/index.js]


Diferencia entre CMD y ENTRYPOINT en un Dockerfile
CMD:


Define el comando o parámetros por defecto del contenedor.


Se sobrescribe fácilmente al ejecutar docker run con otro comando.


Ejemplo:

 CMD ["echo", "Hola Mundo"]


docker run imagen → echo Hola Mundo


docker run imagen echo Adiós → echo Adiós


ENTRYPOINT:


Define el comando principal que siempre se ejecutará.


No se sobrescribe, los argumentos de docker run se añaden al final.


Ejemplo:

 ENTRYPOINT ["echo"]


docker run imagen Hola → echo Hola


docker run imagen Adiós → echo Adiós


Usados juntos:


ENTRYPOINT fija el comando.


CMD define los argumentos por defecto (que pueden cambiarse).


Ejemplo:

 ENTRYPOINT ["echo"]
CMD ["Hola Mundo"]


docker run imagen → echo Hola Mundo


docker run imagen Adiós → echo Adiós



✅ Resumen rápido:
CMD = valores por defecto, reemplazables.


ENTRYPOINT = comando fijo, argumentos variables.


ENTRYPOINT + CMD = comando fijo con parámetros por defecto.

Para taguear un dockerfile:
Docker build -t <nombre_tag>
Donde -t significa que le estas colocando un tag.
