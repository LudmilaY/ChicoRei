FROM php:8.1-fpm-alpine

WORKDIR /app

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install pdo_mysql \
    && docker-php-ext-enable pdo_mysql

COPY composer.* ./
RUN composer install --no-dev --optimize-autoloader

COPY . .

EXPOSE 9000

CMD ["php-fpm"]