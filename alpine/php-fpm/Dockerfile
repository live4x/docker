FROM php:7.4.7-fpm-alpine
RUN  apk add --update --no-cache \
       # dependancies \
       # dependancy for zip \
       libzip \
       # for intl \
       icu-libs libintl \
       # for gd \
       libjpeg libpng freetype \
    && apk add --update --no-cache --virtual .build-deps \
        # for zip \
        libzip-dev \
        # dev deps for gd \
        freetype-dev \
        jpeg-dev \
        libjpeg-turbo-dev \
        libpng-dev \
        # for intl \
        icu-dev \
        # for gettext \
        gettext-dev \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install \
        calendar exif \
        pdo mysqli pdo_mysql zip gd bcmath intl gettext \
    && echo -e "\n opcache.enable=1 \n opcache.enable_cli=1 \n opcache.memory_consumption=128 \n opcache.interned_strings_buffer=8 \n opcache.max_accelerated_files=4000 \n opcache.revalidate_freq=60 \n opcache.fast_shutdown=1" >> /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini \
    && cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*
EXPOSE 9000
