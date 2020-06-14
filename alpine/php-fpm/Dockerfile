FROM php:7.4.7-fpm-alpine
RUN  apk add --update --no-cache libzip-dev \
  && docker-php-ext-install mysqli pdo pdo_mysql zip  \
  && docker-php-ext-enable mysqli pdo pdo_mysql zip \
  && rm -rf /var/cache/apk/*
EXPOSE 9000
