ARG PHP_VERSION

FROM php:${PHP_VERSION}-fpm

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl \
    && docker-php-ext-install pdo pdo_mysql \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug