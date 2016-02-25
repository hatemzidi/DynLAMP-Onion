FROM php:5.6.11-fpm
MAINTAINER Hatem ZIDI <hatem.zidi@gmail.com>

RUN apt-get update && apt-get install -y zlib1g-dev libicu-dev g++ libmcrypt-dev
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install iconv mcrypt

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

RUN docker-php-ext-install exif
#RUN apt-get install -y libldb-dev && docker-php-ext-install ldap
RUN docker-php-ext-install zip

RUN pecl install apcu-4.0.10 \
    && echo extension=apcu.so > /usr/local/etc/php/conf.d/apcu.ini

RUN curl https://pecl.php.net/get/mongo-1.5.8.tgz > /tmp/mongo.tgz
RUN tar -xpzf /tmp/mongo.tgz
RUN mv mongo-1.5.8 /usr/src/php/ext
RUN docker-php-ext-install mongo-1.5.8

RUN apt-get update \
    &&  docker-php-ext-install mbstring pdo_mysql mcrypt mysql
   
ADD conf/www.conf /etc/php5/fpm/pool.d/www.conf
ADD conf/30-custom.ini /usr/local/etc/php/conf.d/30-custom.ini

RUN useradd tom -p tom

RUN apt-get update
RUN apt-get -y install wget

RUN wget http://download.gna.org/wkhtmltopdf/0.12/0.12.2.1/wkhtmltox-0.12.2.1_linux-jessie-amd64.deb 
RUN apt-get -y install xfonts-base xfonts-75dpi xfonts-utils fontconfig libxext6 libfontconfig1 libjpeg62-turbo libx11-6 libxrender1
RUN dpkg -i wkhtmltox-0.12.2.1_linux-jessie-amd64.deb
RUN rm wkhtmltox-0.12.2.1_linux-jessie-amd64.deb

RUN apt-get -y install locales

ENTRYPOINT php-fpm --nodaemonize

VOLUME /var/www

WORKDIR /var/www
