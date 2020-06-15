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
        pdo mysqli pdo_mysql zip gd bcmath intl \
    &&  echo -e "\n opcache.enable=1 \n opcache.enable_cli=1 \n opcache.memory_consumption=128 \n opcache.interned_strings_buffer=8 \n opcache.max_accelerated_files=4000 \n opcache.revalidate_freq=60 \n opcache.fast_shutdown=1" >> /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*
EXPOSE 9000
