FROM php:7.0-fpm-alpine
MAINTAINER Lars Nieuwenhuizen <l.nieuwenhuizen@developers.nl>

RUN docker-php-source extract && \
  apk add --update --no-cache autoconf g++ make && \
  pecl install redis && \
  docker-php-ext-install tokenizer && \
  docker-php-ext-install pdo && \
  docker-php-ext-install mysqli && \
  docker-php-ext-install pdo_mysql && \
  docker-php-ext-install mbstring && \
  docker-php-ext-install curl && \
  docker-php-ext-install dom && \
  docker-php-ext-install xml && \
  docker-php-ext-install xdebug && \
  docker-php-ext-install gd && \
  docker-php-ext-install session && \
  docker-php-ext-enable redis && \
  docker-php-ext-install zip && \
  docker-php-source delete

RUN rm -rf /var/cache/apk/*

# ensure www-data user exists
RUN set -x ; \
  addgroup -g 82 -S www-data ; \
  adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 1

RUN php7 -v

CMD ["-"]