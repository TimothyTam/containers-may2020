FROM mysql:5.7

#Set default value for mysql ROOT. Find this value in mysql in DockerHub
ENV MYSQL_ROOT_PASSWORD=changeit

ADD *.sql /docker-entrypoint-initdb.d/

#Healthcheck First probe is start-period+interval = 35s
HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
   CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1
   
#Where MySQL stores the database
VOLUME /var/lib/mysql/