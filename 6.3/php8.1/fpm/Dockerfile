FROM wordpress:6.3-php8.1-fpm

ENV PHP_SMTP_PORT 25

RUN apt-get update \
 && apt-get install --no-install-recommends -y \
    msmtp libxml2-dev \
 && rm -rf /var/lib/apt/lists/* \
 && docker-php-ext-install soap \
 && pecl install redis && docker-php-ext-enable redis

# Add ability to inject command on container startup
RUN mkdir /docker-entrypoint.d && sed -i '/^exec "$@"/i DIR=/docker-entrypoint.d && if [ -d "$DIR" ]; then /bin/run-parts "$DIR"; fi' /usr/local/bin/docker-entrypoint.sh

# Session management with env var
COPY docker-configure-session /docker-entrypoint.d

# Mail direct sending (mail function)
COPY docker-configure-mail /docker-entrypoint.d

# PHP ini configuration
COPY docker-php-ini-configure /docker-entrypoint.d
