FROM php:8.2-fpm-alpine

RUN set -ex \
  && apk --no-cache add \
    postgresql-dev

RUN docker-php-ext-install pgsql pdo_pgsql

RUN apk add shadow && usermod -u 1000 www-data && groupmod -g 1000 www-data