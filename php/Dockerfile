FROM php:7.4-fpm-alpine
RUN apk add --update linux-headers
RUN apk --no-cache add libxml2-dev pcre-dev jpeg-dev libpng-dev libzip-dev zip ${PHPIZE_DEPS} \
  && pecl install xdebug-3.1.6 \
  && docker-php-ext-enable xdebug \
  && docker-php-ext-configure gd --with-jpeg \
  && docker-php-ext-install mysqli soap pdo_mysql bcmath zip -j$(nproc) gd \
  && apk del pcre-dev ${PHPIZE_DEPS}
COPY ./php/php.ini /usr/local/etc/php/conf.d/infoeduka-custom.ini
COPY ./php/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY ./php/certifikat.pfx /etc/ssl/private/certifikat.pfx