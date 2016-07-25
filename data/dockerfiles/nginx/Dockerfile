FROM nginx:latest

MAINTAINER Ruben Aarts

EXPOSE 80
EXPOSE 443

ADD nginx.conf /etc/nginx/
ADD default.conf /etc/nginx/conf.d/

VOLUME /var/log/nginx

CMD ["nginx"]