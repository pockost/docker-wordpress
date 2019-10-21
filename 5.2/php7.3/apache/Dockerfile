FROM wordpress:5.2-php7.3-apache

RUN pecl install redis && docker-php-ext-enable redis \
    && a2enmod headers