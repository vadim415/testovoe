FROM  centos:7

RUN yum install epel-release -y && yum update -y
RUN yum install -y wget openssl sed &&\
    yum -y autoremove &&\
    yum clean all &&\
    yum install nginx -y
RUN mkdir -p /etc/nginx/conf.d/ && mkdir -p /var/www/html/ && chown nginx:nginx -R  /var/www/html/
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /var/www/html/index.html
COPY vhost.conf /etc/nginx/conf.d/
#RUN mkdir -p /etc/nginx/conf.d/ && chown nginx:nginx -R /etc/nginx/conf.d/ && mkdir -p /var/www/html/

VOLUME [ "/var/www/symfony" ]
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

