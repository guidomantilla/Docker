FROM mysql
ENV MYSQL_DATABASE sample
ENV MYSQL_ROOT_HOST %
ENV MYSQL_ROOT_PASSWORD r00t123!+

COPY ./scripts/ /docker-entrypoint-initdb.d/
EXPOSE 3306
