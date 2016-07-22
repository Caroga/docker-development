FROM nginx:latest

MAINTAINER Ruben Aarts

EXPOSE 80
EXPOSE 443

ADD nginx.conf /etc/nginx/
ADD default /etc/nginx/conf.d/

CMD ["nginx"]