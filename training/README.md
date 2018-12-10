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
1. docker volume ls

Para ahorrar un poco de escritura, vamos a crear un archivo **sh** que ejecutara varios comandos al tiempo, asi:
1. Ejecutamos: **touch docker-show-env.sh**
1. Ejecutamos: **nano docker-show-env.sh**
1. Escribir: **echo && docker image ls && echo && docker container ls -a && echo && docker network ls && echo && docker volume ls**
1. Guardamos.
1. Ejecutamos: **sh docker-show-env.sh** 

Nota: De aqui en adelante, cuando se indique que se debe ejecutar **sh docker-show-env.sh**  se debera tener en cuenta la ubicacion relativa de donde estamos ubicados respecto a la ubicacion del archivo SH.