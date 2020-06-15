FROM php:7.4.7-fpm-alpine
RUN  apk add --update --no-cache --virtual .build-deps \
        libzip-dev \
        # dev deps for gd \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
        # for intl \
        icu-dev \
    && docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install \
    &&   pdo mysqli pdo_mysql zip gd bcmath intl \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*
EXPOSE 9000
