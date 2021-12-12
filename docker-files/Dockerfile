FROM php:7.2-fpm

RUN apt-get update \
    && apt-get install -y \
        libc-client2007e-dev \
        libkrb5-dev \
        libwebp-dev \
        libxml2-dev \
        libjpeg-dev \
        libpng-dev \
        unzip \
    && docker-php-ext-configure gd \
        --with-webp-dir \
        --with-jpeg-dir \
    && docker-php-ext-configure imap \
        --with-kerberos \
        --with-imap-ssl \
    && docker-php-ext-install gd soap imap zip pdo_mysql \
    && pecl install xdebug-2.9.6 \
    && docker-php-ext-enable xdebug \
    && mv /usr/local/etc/php/php.ini-development \
          /usr/local/etc/php/php.ini \
    && curl https://getcomposer.org/download/1.10.24/composer.phar \
         -o /usr/local/bin/composer \
    && chmod a+x /usr/local/bin/composer

COPY xdebug.ini /usr/local/etc/php/conf.d/

EXPOSE 8000
