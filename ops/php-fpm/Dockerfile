# Use the official PHP 8.2 FPM Alpine image as the base image
FROM php:8.2-fpm-alpine

# Install required dependencies, including PostgreSQL development files
RUN set -ex \
  && apk --no-cache add \
    postgresql-dev

# Install the PHP PostgreSQL extensions
RUN docker-php-ext-install pgsql pdo_pgsql

# Install the 'shadow' package and modify the 'www-data' user and group IDs
RUN apk add shadow && usermod -u 1000 www-data && groupmod -g 1000 www-data

# Download and install Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
  && rm composer-setup.php

# Set Composer as executable
RUN chmod +x /usr/local/bin/composer

# Define the working directory for your PHP application
WORKDIR /var/www/html