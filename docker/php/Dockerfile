# PHP7.3をインストール
FROM php:7.3-fpm

# ローカルにあるphp.ini → Docker /usr/local/etc/php/php.ini
COPY ./php.ini /usr/local/etc/php/php.ini

RUN pecl install xdebug

RUN docker-php-ext-enable xdebug
  
RUN apt-get update \
  && apt-get install -y && apt-get install -y libzip-dev && apt-get install -y zlib1g-dev mariadb-client \
  && docker-php-ext-install zip pdo_mysql

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

# /var/www
WORKDIR /var/www

# Laravelをインストール
# docker-compose exec php bashでログインして下のコマンドを打つ
# composer create-project laravel/laravel portfolio --prefer-dist "6.*"  
# http://localhost:8081
