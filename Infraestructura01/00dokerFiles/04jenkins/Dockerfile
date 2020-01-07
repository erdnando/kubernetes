FROM jenkins/jenkins:lts
USER root

RUN mkdir -p /tmp/download && \
 curl -L https://download.docker.com/linux/static/stable/x86_64/docker-19.03.5.tgz | tar -xz -C /tmp/download && \
 rm -rf /tmp/download/docker/dockerd && \
 mv /tmp/download/docker/docker* /usr/local/bin/ && \
 rm -rf /tmp/download && \
 groupadd -g 999 docker && \
 usermod -aG staff,docker jenkins


#VOLUME /var/run/docker.sock/
#/var/jenkins_home/

USER jenkins




#make repository in docker-hub : erdnando/jenkins-fintech
#docker rmi image erdnando/jenkins-fintech
#build
#docker build -t erdnando/jenkins-fintech:latest .
#local test
#docker run -it -p 8080:80 --name jenkins-fintech jenkins/jenkins-fintech
#push
#docker push erdnando/jenkins-fintech:latest

# minikube ssh sudo chown 1000 /data/docker-pvy
#minikube ssh sudo chown 1000 /data/jenkins-pvy
#8472df88cede49f492af6de28f963961
