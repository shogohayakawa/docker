FROM php:7.4-apache

WORKDIR /var/www/html/

# PHP 関連ライブラリ
RUN apt-get update \
    && apt-get install -y libonig-dev libzip-dev unzip mariadb-client libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-install pdo_mysql mysqli mbstring zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# composer
COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1

# LaravelのmodRewrite有効化
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite

# ファイルコピー
COPY ./src /var/www/html/
COPY ./docker/app/php.ini /usr/local/etc/php/php.ini
COPY ./docker/app/000-default.conf /etc/apache2/sites-enabled/

# Laravelプロジェクトの権限の変更
RUN chmod 777 -R /var/www/html/bootstrap/cache
