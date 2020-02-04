FROM jboss/wildfly:10.1.0.Final

ADD https://downloads.mariadb.com/Connectors/java/connector-java-1.5.9/mariadb-java-client-1.5.9.jar /opt/jboss/wildfly/modules/system/layers/base/org/mariadb/jdbc/main/
COPY librerias/module.xml /opt/jboss/wildfly/modules/system/layers/base/org/mariadb/jdbc/main/
ADD aplicacion/Aplicacion.war /opt/jboss/wildfly/standalone/deployments/

RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#123 --silent

EXPOSE 9990

VOLUME /opt/jboss/wildfly/standalone/deployments/

USER jboss

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]


#make repository in docker-hub : erdnando/backend-fintech
#docker rmi image erdnando/backend-fintech
#build
#docker build -t erdnando/backend-fintech:latest .
#local test
#docker run -it -p 8080:80 --name backend-fintech backend/db-fintech
#push
#docker push erdnando/backend-fintech:latest


 #add to docker daemon settings --> mx.com.smi.services:30402
 #docker login -u admin -p admin mx.com.smi.services:30402
 
 #docker pull erdnando/backend-fintech
 #docker tag erdnando/backend-fintech mx.com.smi.services:30402/backend-fintech:latest
 #docker push mx.com.smi.services:30402/backend-fintech:latest