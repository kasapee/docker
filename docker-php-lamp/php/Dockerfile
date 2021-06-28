FROM centos:centos6.9

# ENV PHP_VERSION 5.3.1
RUN export PHP_VERSION=5.3.1

# CentOS6系のサポート切れによるyumコマンド対処
RUN sed -i "s|#baseurl=|baseurl=|g" /etc/yum.repos.d/CentOS-Base.repo \
  && sed -i "s|mirrorlist=|#mirrorlist=|g" /etc/yum.repos.d/CentOS-Base.repo \
  && sed -i "s|http://mirror\.centos\.org/centos/\$releasever|https://vault\.centos\.org/6.6|g" /etc/yum.repos.d/CentOS-Base.repo

RUN yum install -y \
        php \
        php-mbstring \
        php-pgsql \
        php-mysql \
        php-gd \
        zip \
        unzip \
        git \
        httpd && \
    yum clean all

# RUN pecl channel-update pecl.php.net && \
#     pecl install xdebug-2.2.7

RUN mkdir /app
WORKDIR /app

EXPOSE 80

CMD ["/usr/sbin/apachectl","-DFOREGROUND"]