FROM php:8-fpm-alpine

ENV TZ=Asia/Hong_Kong
ENV WORKDIR=/var/www/app

RUN apk add --update --no-cache bash tzdata libxml2-dev libxslt-dev freetype-dev oniguruma-dev libzip-dev $PHPIZE_DEPS && rm -rf /var/cache/apk/*

RUN docker-php-ext-install zip exif 

RUN pecl install xdebug && docker-php-ext-enable xdebug

COPY ./conf.d ${PHP_INI_DIR}/conf.d

WORKDIR ${WORKDIR}

EXPOSE 9000

COPY ./entrypoint.sh /usr/bin/docker-entrypoint
CMD [ "docker-entrypoint" ]
