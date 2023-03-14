FROM php:8.1-fpm-alpine
WORKDIR /var/www/html

RUN apk update

RUN apk add libzip-dev

RUN docker-php-ext-install mysqli zip pdo pdo_mysql exif && docker-php-ext-enable pdo_mysql

COPY ./src /var/www/html

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN chown -R www-data:www-data /var/www/html/storage && \
    chmod -R 777 /var/www/html/storage

ENTRYPOINT ["docker-php-entrypoint"]
USER www-data
CMD ["php-fpm"]

EXPOSE 9000