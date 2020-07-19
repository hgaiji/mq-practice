FROM php:7.3-fpm

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
COPY composer.json ./
RUN apt-get update \ 
    && apt-get install -y zlib1g-dev -y libzip-dev\
    && docker-php-ext-install zip bcmath sockets
RUN composer self-update 
RUN composer install
CMD [ "php", "./receive.php" ]