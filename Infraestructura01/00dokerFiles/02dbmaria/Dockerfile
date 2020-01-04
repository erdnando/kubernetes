FROM mariadb:10.1.22

ENV MYSQL_ROOT_PASSWORD admin123
ENV MYSQL_DATABASE curso

ADD datos/cargaDatos.sql /docker-entrypoint-initdb.d/cargaDatos.sql


#make repository in docker-hub : erdnando/db-fintech
#docker rmi image erdnando/db-fintech
#build
#docker build -t erdnando/db-fintech:latest .
#local test
#docker run -it -p 8080:80 --name db-fintech erdnando/db-fintech
#push
#docker push erdnando/db-fintech:latest
