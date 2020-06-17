ARG PHP_IMAGE_TAG=7.3-1.x
FROM srijanlabs/php-cli:${PHP_IMAGE_TAG} as builder
COPY composer.json composer.lock /app/
COPY patches ./patches
RUN composer install --no-dev --prefer-dist --no-progress --no-suggest --no-interaction --optimize-autoloader

FROM srijanlabs/php-fpm-apache:${PHP_IMAGE_TAG} as fpm
COPY --from=builder --chown=continua /app  /app
COPY --chown=continua . /app