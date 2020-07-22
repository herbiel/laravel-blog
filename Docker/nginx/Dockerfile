FROM centos:7
RUN yum install epel-release -y\
    && yum install nginx -y
RUN mkdir -p /app  \
    && sed -i 's#user nginx;#user nobody;#g' /etc/nginx/nginx.conf
COPY laravel.conf /etc/nginx/conf.d/
CMD [ "nginx", "-g", "daemon off;" ]