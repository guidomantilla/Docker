# Docker Training
Curso de Docker.

## Prerequisitos
1. Verificar que el equipo este habilitado para la virtualizacion (revisar la BIOS)
1. Verificar que se tenga instalado Git Bash. Una vez hecho esto ejecutar:
    - ssh-keygen -t rsa -b 4096 -C 'su.correo@electronico.porfavor'
    - ls -al ~/.ssh 
    - eval "$(ssh-agent -s)" 
    - ssh-add ~/.ssh/id_rsa  
1. Clonar este repositorio localmente: https://github.com/guidomantilla/Docker.git
1. Abrir el archivo Docker Slides.PDF
1. Descargar el archivo vdi desde https://drive.google.com/open?id=17jgS5cZHT6shF4CVO-G0-1zuRETB_VV5
1. Descargar e instalar Virtual Box (https://www.virtualbox.org/)
1. Crear una maquina virtual con las siguientes caracteristicas:
    - RAM: **4GB**
    - Adaptador de Red 1: **NAT**
    - Adaptador de Red 2: **Host Only**
    - Carpetas compartidas: **Seleccionar una del Disco Duro del Equipo**
1. Iniciar la maquina virtual en modo **Desacomplado**
1. Usando Git Bash, ingresamos a la maquina virtual usando el comando **ssh osboxes@[VM IP]**. La contraseña es **osboxes.org**

## Comandos Basicos Docker
Los comandos basicos para ver el estado del docker engine local:
1. docker image ls
1. docker container ls -a
1. docker network ls

Para ahorrar un poco de escritura, vamos a crear un archivo **sh** que ejecutara varios comandos al tiempo, asi:
1. Ejecutamos: **touch docker-show-env.sh**
1. Ejecutamos: **nano docker-show-env.sh**
1. Escribir: **echo && docker image ls && echo && docker container ls -a && echo && docker network ls && echo**
1. Guardamos.
1. Ejecutamos: **sh docker-show-env.sh** 


## Primer Contenedor Docker
Aqui vamos a crear nuestro primer contenedor docker. En esta ocasion el contenedor ejecutara un aplicativo Spring Boot de ejemplo.
1. Ejecutamos: **cd workspaces/java/sample.web**
1. Ejecutamos: **mvn clean install**
1. Ejecutamos: **cat Dockerfile**
1. Ejecutamos: **docker build -t sample.web .**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Ejecutamos: **docker container run --publish 9090:9090 --detach --name sample.web sample.web**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:9090/dummies**
1. Para detener el contenedor, ejecutamos: **docker container stop sample.web**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.web**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.web**
    - **docker container top sample.web**
    - **docker container stats sample.web**
    - **docker container logs sample.web**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.web sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:9090/dummies**
1. Para eliminar el contenedor, ejecutamos: **docker container rm sample.web** o **docker container rm -f sample.web**
1. Ejecutamos: **sh docker-show-env.sh** 

## Segundo Contenedor Docker
1. Ejecutamos: **cd workspaces/node/ChatApp**
1. Ejecutamos: **cat Dockerfile**
1. Ejecutamos: **docker build -t sample.chat .**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Ejecutamos: **docker container run --publish 3000:3000 --detach --name sample.chat sample.chat**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:3000/**
1. Para detener el contenedor, ejecutamos: **docker container stop sample.chat**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.chat**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.chat**
    - **docker container top sample.chat**
    - **docker container stats sample.chat**
    - **docker container logs sample.chat**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.chat sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:3000/**
1. Para eliminar el contenedor, ejecutamos: **docker container rm sample.chat** o **docker container rm -f sample.chat**
1. Ejecutamos: **sh docker-show-env.sh** 

## Tercer Contenedor Docker
1. Ejecutamos: **cd workspaces/react/sample.react**
1. Ejecutamos: **cat Dockerfile**
1. Ejecutamos: **docker build -t sample.react .**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Ejecutamos: **docker container run --publish 80:80 --detach --name sample.react sample.react**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]/**
1. Para detener el contenedor, ejecutamos: **docker container stop sample.react**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.react**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.react**
    - **docker container top sample.react**
    - **docker container stats sample.react**
    - **docker container logs sample.react**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.react sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]**
1. Para eliminar el contenedor, ejecutamos: **docker container rm sample.react** o **docker container rm -f sample.react**
1. Ejecutamos: **sh docker-show-env.sh** 

## Api Rest Contenedores Docker
Primero creamos un contenedor para la base de datos MySQL:
1. Ejecutamos: **cd workspaces/mysql**
1. Ejecutamos: **cat Dockerfile**
1. Ejecutamos: **cat scripts/CreateTable.sql**
1. Ejecutamos: **docker build -t sample.db .**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Ejecutamos: **docker container run --publish 3306:3306 --detach --name sample.db sample.db**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para detener el contenedor, ejecutamos: **docker container stop sample.db**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.db**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.db**
    - **docker container top sample.db**
    - **docker container stats sample.db**
    - **docker container logs sample.db**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.db sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Ejecutamos: **sh docker-show-env.sh** 

Segundo creamos otro contenedor para el API Rest:
1. Ejecutamos: **cd workspaces/java/sample.ws**
1. Ejecutamos: **cat Dockerfile**
1. Ejecutamos: **docker build -t sample.ws .**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Ejecutamos: **docker container run --publish 9091:9091 --link sample.db:mysql_db --detach --name sample.ws sample.ws**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:9091/sample.ws/api/employees**
1. De ser necesario, ingresamos user y password:
    - osboxes
    - osboxes.org
1. Para detener el contenedor, ejecutamos: **docker container stop sample.ws**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.ws**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.ws**
    - **docker container top sample.ws**
    - **docker container stats sample.ws**
    - **docker container logs sample.ws**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.ws sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Ejecutamos: **sh docker-show-env.sh** 
1. En el navegador del equipo, ingresamos: **http://[VM IP]:9091/sample.ws/api/employees**
1. Para eliminar el contenedor API Rest, ejecutamos: **docker container rm sample.ws** o **docker container rm -f sample.ws**
1. Ejecutamos: **sh docker-show-env.sh** 
1. Para eliminar el contenedor Mysql, ejecutamos: **docker container rm sample.db** o **docker container rm -f sample.db**
1. Ejecutamos: **sh docker-show-env.sh**