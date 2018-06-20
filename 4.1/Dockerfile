FROM php:7.2-fpm-alpine

RUN set -xe \
    && apk add --update icu \
    && apk add --no-cache --virtual .php-deps make \
    && apk add --no-cache --virtual .build-deps \
        $PHPIZE_DEPS \
        zlib-dev \
        icu-dev \
        g++ \
    && curl -sS -o /tmp/icu.tar.gz -L http://download.icu-project.org/files/icu4c/61.1/icu4c-61_1-src.tgz && tar -zxf /tmp/icu.tar.gz -C /tmp && cd /tmp/icu/source && ./configure --prefix=/usr/local && make && make install \
    && docker-php-ext-configure intl --with-icu-dir=/usr/local \
    && docker-php-ext-install intl \
    && docker-php-ext-enable intl \
    && { find /usr/local/lib -type f -print0 | xargs -0r strip --strip-all -p 2>/dev/null || true; } \
    && apk del .build-deps \
    && rm -rf /tmp/* /usr/local/lib/php/doc/* /var/cache/apk/*

RUN docker-php-ext-install opcache
COPY ./php.ini /usr/local/etc/php/php.ini
