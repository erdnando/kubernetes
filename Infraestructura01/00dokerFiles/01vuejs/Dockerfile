FROM node:8.16.2 as builder


#https://itnext.io/building-docker-images-from-private-git-repositories-using-ssh-login-433edf5a18f2


COPY github_key .
RUN eval $(ssh-agent) && \
    ssh-add github_key && \
    ssh-keyscan -H github.com >> /etc/ssh/ssh_known_hosts && \
    git clone git@github.com:erdnando/afiliacion2.0.git /opt/vue_app

WORKDIR /opt/vue_app
RUN npm install && npm run build


# Stage 1, based on Nginx, to have only the compiled app, ready for production with Nginx
FROM nginx:1.17.6

#Copy ci-dashboard-dist
COPY --from=builder /opt/vue_app/dist/ /usr/share/nginx/html/fintech/

#Copy images folder to root
RUN cp -R /usr/share/nginx/html/fintech/images /usr/share/nginx/html/images
#Copy facephi folder to root
RUN cp -R /usr/share/nginx/html/fintech/facephi /usr/share/nginx/html/facephi
#Add folder to container
ADD ./img /usr/share/nginx/html/img

#COPY shell to update html index
#COPY update-html.sh /usr/share/nginx/html/fintech/
#RUN chmod 777 /usr/share/nginx/html/fintech/update-html.sh
#RUN /usr/share/nginx/html/fintech/update-html.sh


RUN chmod -R 777 /usr/share/nginx/html/fintech
RUN chmod -R 777 /usr/share/nginx/html/images
RUN chmod -R 777 /usr/share/nginx/html/img



#docker rmi image erdnando/front-fintech
#build
#docker build -t erdnando/front-fintech:latest .
#local test
#docker run -it -p 8080:80 --name web-vue erdnando/front-fintech
#push
#docker push erdnando/front-fintech:latest


EXPOSE 80
#Copy default nginx configuration
COPY ./nginx-custom.conf /etc/nginx/conf.d/default.conf
