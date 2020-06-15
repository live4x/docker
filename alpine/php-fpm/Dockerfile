FROM php:7.4.7-fpm-alpine
RUN  apk add --update --no-cache \
       # dependancies \
       # dependancy for zip \
       libzip \
       # for intl \
       icu-libs libintl \
       # for gd \
       libjpeg libpng freetype \
       # for xml \
       libxml2 \
       # for xsl \
       libxslt \
       # for ldap \
       libldap \
       # for imap \
       c-client \
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
        # for soap \
        libxml2-dev \
        # for xsl \
        libxslt-dev \
        # for ldap \
        openldap-dev \
        # for imap \
        imap-dev \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install \
        calendar exif \
        pdo mysqli pdo_mysql zip gd bcmath intl gettext soap xsl xmlrpc ldap imap \
    && docker-php-ext-enable opcache \
    && cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini \
    && sed -i "s/^;opcache.enable=.*/opcache.enable=1/g" /usr/local/etc/php/php.ini \
    && sed -i "s/^;opcache.enable_cli=.*/opcache.enable_cli=1/g" /usr/local/etc/php/php.ini \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*
EXPOSE 9000
