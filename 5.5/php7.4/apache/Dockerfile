FROM wordpress:5.5-php7.4-apache

RUN pecl install redis && docker-php-ext-enable redis \
    && a2enmod headers

# Add ability to inject command on container startup
RUN mkdir /docker-entrypoint.d
COPY docker-entrypoint.sh /usr/local/bin/

# Session management with env var
COPY docker-configure-session /docker-entrypoint.d

# HTTP expires headers
COPY expires.conf /etc/apache2/conf-enabled/expires.conf

# PHP upload size
RUN echo -n "upload_max_filesize = 64M\npost_max_size = 128M" > /usr/local/etc/php/conf.d/upload.ini
