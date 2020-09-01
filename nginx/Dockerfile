FROM centos:centos7

LABEL maintainer="pingink <pingink@163.com>"

ENV NGINX_VERSION="1.14.0-1" \
    OS="centos" \
    OS_VERSION="7" \
    EL_VERSION="7_4"

RUN yum install -y wget openssl sed &&\
    yum -y autoremove &&\
    yum clean all &&\
    wget http://nginx.org/packages/$OS/$OS_VERSION/x86_64/RPMS/nginx-$NGINX_VERSION.el$EL_VERSION.ngx.x86_64.rpm &&\
    rpm -iv nginx-$NGINX_VERSION.el$EL_VERSION.ngx.x86_64.rpm

COPY nginx.conf /etc/nginx/

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
