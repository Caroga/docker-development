FROM nginx:latest

MAINTAINER Ruben Aarts

RUN ln -s /etc/nginx/sites-available/* /etc/nginx/sites-enabled/*

EXPOSE 80
EXPOSE 443

ADD nginx.conf /etc/nginx/
ADD default /etc/nginx/conf.d/

VOLUME ${PWD}/config/nginx:/etc/nginx/sites-available

CMD ["nginx"]