FROM php:5.6-apache
COPY docker-php-pecl-install /usr/local/bin/

RUN apt-get update && apt-get install -y \
 libfreetype6-dev \
 libjpeg62-turbo-dev \
 libmcrypt-dev \
 libpng12-dev \
 libicu-dev \
 git \
 zip \
 libzip-dev \
    && docker-php-ext-install intl pdo_mysql mcrypt mbstring zip calendar \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-pecl-install xdebug-2.3.3

RUN a2enmod rewrite
RUN usermod -u 1000 www-data
COPY config/php.ini /usr/local/etc/php/
COPY config/vhost/vhost.conf /etc/apache2/sites-enabled/