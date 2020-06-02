FROM wordpress:4.9-php7.0-apache

RUN pecl install redis && docker-php-ext-enable redis \
    && a2enmod headers