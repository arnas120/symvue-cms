FROM php:8.3-fpm

ARG user
ARG uid
ARG xdebug

COPY "./" "/var/www/"
COPY .docker/php-fpm/php.ini /usr/local/etc/php/conf.d/php.ini
COPY .docker/php-fpm/opcache.ini /usr/local/etc/php/conf.d/opcache.ini

RUN apt-get update && apt-get install -y \
    git \
    curl \
    libcurl3-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libjpeg-dev \
    libwebp-dev \
    zip \
    unzip \
    curl

RUN docker-php-ext-install curl pdo_mysql mbstring exif pcntl bcmath gd

# imagick
RUN docker-php-ext-install opcache

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# node js
RUN curl -sL https://deb.nodesource.com/setup_20.x | bash -
RUN apt install -y nodejs

COPY .docker/php-fpm/xdebug.ini /tmp/
RUN pecl install xdebug
RUN mv /tmp/xdebug.ini /usr/local/etc/php/conf.d/


RUN chmod -R 777 /var/www/


WORKDIR /var/www/

