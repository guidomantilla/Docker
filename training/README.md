# Docker Training
Curso de Docker.

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