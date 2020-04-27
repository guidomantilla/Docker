FROM mysql
ENV MYSQL_DATABASE='sample' \
    MYSQL_ROOT_HOST='%' \
    MYSQL_ROOT_PASSWORD='r00t123!+' \
    MYSQL_USER='raven' \
    MYSQL_PASSWORD='r4v3n123+'
    
COPY ./scripts/ /docker-entrypoint-initdb.d/
EXPOSE 3306 33060
