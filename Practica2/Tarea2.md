## Parte 1

Para crear el volumen usamos `docker volume create DockerVolume`

Para usar el servidor de nginx 
`docker run --name nginx -d -p 80:80 --mount source=DockerVolume,target=/usr/share/nginx/html nginx`

`docker run --name nginx2 -d -p 80:81 --mount source=DockerVolume,target=/usr/share/nginx/html nginx`

Modificando el arvicho index.html

![Captura Browser](./img/Browser)

## Parte 2

docker network create redDocker
Para hacer el ping y conocer la ip es necesario instalar net-tools y inetutils-ping.
`docker run --name Ubuntu1 -d -t --network redDocker ubuntu /bin/bash`

`docker run --name Ubuntu2 -d -t ubuntu /bin/bash`

El primer ping no funciona debido a que los contenedores estan en diferentes redes, tenemos que conectar Ubuntu2 a la misma red que Ubuntu1.

Para ello usamos el comando
`docker network connect redDocker Ubuntu`

Ahora si hacemos ping desde Ubuntu1 funconaría pues los dos se encontrarían en la misma red.
![Imagen Ping](./img/Ping)
