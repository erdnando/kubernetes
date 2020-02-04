# minikube ssh sudo chown 1000 /data/docker-pvy
#minikube ssh sudo chown 1000 /data/jenkins-pvy
#8472df88cede49f492af6de28f963961

watch -n1 kubectl get all


- Crear el docker file
- docker build -t hello-node:v1 .    <---punto
- docker tag hello-node:v1 erdnando/hello-node:latest
- crear en docker hub repositorio con el nombre deseado y que coincida con el tag, latest 
- docker push erdnando/hello-node:latest

    nginx.ingress.kubernetes.io/rewrite-target: /$1
    sed -i -e "s/href=\//href=\/fintech\//g" /usr/share/nginx/html/fintech/index.html

sed -i -e "s/src=\//src=\/fintech\//g" /usr/share/nginx/html/fintech/index.html

/etc/init.d/nginx restart

watch -n1 kubectl get all
cat /etc/os-release
------------------------------------------------------------------------------------------------
minikube config set memory 10240
minikube config set cpus 3
minikube config set disk-size 60000MB
minikube config set vm-driver virtualbox
minikube delete
minikube start
minikube start --insecure-registry="mx.com.smi.services:30402"

minikube addons enable metrics-server


minikube ssh
 minikube addons list
 minikube dashboard
 minikube stop
minikube ip
------------------------------------------------------------------------------------------------
https://itnext.io/building-docker-images-from-private-git-repositories-using-ssh-login-433edf5a18f2


nginx common path ->  /usr/share/nginx/html/
nginx.ingress.kubernetes.io/app-root: /app1
https://kubernetes.github.io/ingress-nginx/examples/rewrite/
------------------------------------------------------------------------------------------------

secrets

kubectl get secrets

kubectl get secrets -n kube-system

kubectl create secret generic credenciales --from-file=./username.txt --from-file=password.txt

kubectl describe secret credenciales

kubectl get secret credenciales -o yaml

echo -n jdbc:mysql://mx.com.smi.services:30201/curso > urlbackend.txt
echo -n root > username.txt
echo -n admin123 > password.txt
base64 urlbackend.txt > urlbackend64.txt
base64 username.txt > username64.txt 
base64 password.txt > password64.txt

watch -n1 kubectl get all
minikube service db-lb-a --url

#http://mx.com.smi.services:30101/Aplicacion/aplicacion




- protocol: "TCP"
    # Port accessible inside cluster
    port: 8080
    # Port to forward to inside the pod
    targetPort: 8080
    # Port accessible outside cluster




    
> 
apiVersion: v1
data:
  password.txt: MTIzNTZhYmNk
  username.txt: YWRtaW4=
kind: Secret
metadata:
  creationTimestamp: "2019-12-14T19:59:36Z"
  name: credenciales
  namespace: default
  resourceVersion: "115166"
  selfLink: /api/v1/namespaces/default/secrets/credenciales
  uid: 98ebaaf3-04e0-45fe-9cae-5f6072db8983
type: Opaque


kubectl create secret generic ssh-key-secret --from-file=/home/erdnando/.ssh/id_rsa --from-file=p/home/erdnando/.ssh/id_rsa.pub
------------------------------------------------------------------------------------------------





















---------------------------------------------------------------------------------------

FROM node:8.11.4

RUN mkdir /app
WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

CMD ["npm", "start"] # <<<<<<< We need to change this
------------------------------------------------------------------------------------------
# Stage 0, "build-stage", based on Node.js, to build and compile the frontend
FROM node:10.8.0 as build-stage
WORKDIR /app
COPY package*.json /app/
RUN npm install
COPY ./ /app/
ARG configuration=production
RUN npm run build -- --output-path=./dist/out --configuration $configuration

# Stage 1, based on Nginx, to have only the compiled app, ready for production with Nginx
FROM nginx:1.15
#Copy ci-dashboard-dist
COPY --from=build-stage /app/dist/out/ /usr/share/nginx/html
#Copy default nginx configuration
COPY ./nginx-custom.conf /etc/nginx/conf.d/default.conf
----------------------------------------------------------------------------------------------------------
FROM ubuntu

MAINTAINER Luke Crooks "luke@pumalo.org"

# Update aptitude with new repo
RUN apt-get update

# Install software 
RUN apt-get install -y git
# Make ssh dir
RUN mkdir /root/.ssh/

# Copy over private key, and set permissions
# Warning! Anyone who gets their hands on this image will be able
# to retrieve this private key file from the corresponding image layer
ADD id_rsa /root/.ssh/id_rsa

# Create known_hosts
RUN touch /root/.ssh/known_hosts
# Add bitbuckets key
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

# Clone the conf files into the docker container
RUN git clone git@bitbucket.org:User/repo.git
------------------------------------------------------------------------------------




http://mx.com.smi.services:30001/fintech















