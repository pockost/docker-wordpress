FROM wordpress:5.3-php7.3-apache

RUN pecl install redis && docker-php-ext-enable redis \
    && a2enmod headers