# Docker Basics
1. Abrimos el archivo Docker Slides.PDF
1. Seguimos los siguientes tutoriales.

## Primer Contenedor Docker
Aqui vamos a crear nuestro primer contenedor docker. En esta ocasion el contenedor ejecutara un aplicativo Spring Boot de ejemplo.
Se deberan los siguentes pasos asi:

1. Vamos a la raiz del proyecto JAVA a contruir: **cd workspaces/java/sample.web**
1. Construimos el proyecto JAVA: **mvn clean install**
1. Verificamos el contenido del Dockerfile: **cat Dockerfile**
1. Construimos la imagen Docker con el programa JAVA dentro: **docker build -t sample.web .**
1. Ejecutamos: **sh docker-show-env.sh** (tomar en cuenta la ubicacion relativa)
1. Creamos un nuevo contenedor a partir de la imagen construida: **docker container run --publish 9090:9090 --detach --name sample.web sample.web**
1. Ejecutamos: **sh docker-show-env.sh** (tomar en cuenta la ubicacion relativa)

1. En el navegador del equipo, ingresamos: **http://[VM IP]:9090/dummies**
1. Para detener el contenedor, ejecutamos: **docker container stop sample.web**
1. Ejecutamos: **sh docker-show-env.sh** (tomar en cuenta la ubicacion relativa)
1. Para volver a iniciar el contenedor, ejecutamos: **docker container start sample.web**
1. Ejecutamos: **sh docker-show-env.sh** (tomar en cuenta la ubicacion relativa)
1. En el navegador del equipo, ingresamos: **http://[VM IP]:9090/dummies**

1. Para monitorear el contenedor, ejecutamos:
    - **docker container inspect sample.web**
    - **docker container top sample.web**
    - **docker container stats sample.web**
    - **docker container logs sample.web**
1. Para ingresar al shell del contenedor, ejecutamos: **docker container exec -it sample.web sh**
1. Para salir del shell del contenedor, ejecutamos **exit**
1. Para eliminar el contenedor, ejecutamos: **docker container rm sample.web** o **docker container rm -f sample.web**
1. Ejecutamos: **sh docker-show-env.sh** (tomar en cuenta la ubicacion relativa)

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