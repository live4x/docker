  1 FROM php:7.4.7-fpm-alpine
  2 RUN apk add --update --no-cache libzip-dev \
  3  && docker-php-ext-install mysqli pdo pdo_mysql zip  \
  4  && docker-php-ext-enable mysqli pdo pdo_mysql zip \
  5  && rm -rf /var/cache/apk/*
  6 EXPOSE 9000
