FROM php:7.3-fpm

WORKDIR /var/www

RUN rm -rf /var/www/

RUN apt-get update
RUN apt-get -yq install git

RUN apt-get install -y \
        libzip-dev \
        zip \
  && docker-php-ext-configure zip --with-libzip \
  && docker-php-ext-install zip
RUN docker-php-ext-install pdo_mysql

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get -yq install sudo

RUN curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
RUN apt-get install -y nodejs

RUN apt-get -yq install curl
RUN curl -o- -L https://yarnpkg.com/install.sh | bash

COPY php/config/ /usr/local/etc/php/conf.d/
