FROM php:7.0-fpm
MAINTAINER Matheus Fidelis <msfidelis01@gmail.com>

RUN echo 'deb http://httpredir.debian.org/debian jessie contrib' >> /etc/apt/sources.list
RUN echo 'deb http://packages.dotdeb.org jessie all' >> /etc/apt/sources.list

RUN apt-get update --force-yes
RUN export DEBIAN_FRONTEND=noninteractive && apt-get install -y --force-yes openssl curl libmcrypt-dev libcurl4-gnutls-dev libxml2-dev libicu-dev 

#CONFIGURAÇÕES DO OPCACHE
RUN docker-php-ext-install opcache

#CONFIGURAÇÕES DO APCU
RUN pecl install apcu-5.1.5 && docker-php-ext-enable apcu

#LIBS EXTRAS
RUN apt-get install libmcrypt-dev libreadline-dev -y
RUN docker-php-ext-install bcmath
#RUN docker-php-ext-install bz2
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install mcrypt
RUN apt-get install -y libpq-dev
RUN apt-get install -y libicu-dev
RUN pecl install intl
RUN docker-php-ext-install intl

#GD
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd

#PDO - CUSTOMIZAR A SEU DISPOR
RUN docker-php-ext-install pdo_mysql

EXPOSE 9000
CMD ["php-fpm"]
