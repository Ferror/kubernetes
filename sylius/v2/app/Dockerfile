FROM php:8.0-fpm-alpine AS php-image

COPY --from=composer:2.3 /usr/bin/composer /usr/bin/composer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/bin/install-php-extensions

RUN install-php-extensions \
    calendar \
    ctype \
    curl \
    dom \
    exif \
    gd \
    hash \
    iconv \
    intl \
    mbstring \
    opcache \
    pdo \
    pdo_mysql \
    pdo_pgsql \
    pdo_sqlite \
    pgsql \
    xml \
    xsl \
    zip

RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* /usr/share/man/* /var/cache/apk/*

RUN mkdir -p /var/log/php-fpm/

COPY .docker/fpm.conf   /usr/local/etc/php-fpm.conf
COPY .docker/php.ini    /usr/local/etc/php/php.ini

EXPOSE 9000

CMD ["/usr/local/sbin/php-fpm"]

COPY . /app

RUN composer install --no-scripts --no-interaction --no-dev --no-progress
RUN php bin/console cache:warmup --no-debug --env=prod # --no-optional-warmers

RUN php bin/console doctrine:database:create --if-not-exists
RUN php bin/console sylius:install --no-interaction
RUN php bin/console sylius:fixtures:load default --no-interaction

RUN yarn install --ignore-scripts && yarn add node-sass && yarn build

RUN mkdir -p public/media/image/
RUN chmod -R 777 var/

FROM nginx:1.21-alpine AS nginx-image

COPY .docker/nginx.conf /etc/nginx/nginx.conf
COPY --from=php-image /app /app
