FROM alpine:3.5
MAINTAINER Lars Nieuwenhuizen <l.nieuwenhuizen@developers.nl>

RUN	echo "http://dl-cdn.alpinelinux.org/alpine/latest-stable/releases" >> /etc/apk/repositories && \
    apk update && \
	apk upgrade && \
	apk add --no-cache --update \
		php7-mbstring \
		php7-pdo \
		php7-soap \
		php7-mcrypt \
		php7-openssl \
		php7-json \
		php7-dom \
		php7-xml \
		php7-pdo_mysql \
		php7-gettext \
		php7-iconv \
		php7-curl \
		php7-zip \
		php7-ctype \
		php7-session \
		php7-gd \
		php7-xdebug \
		php7-redis \
		php7-fpm

RUN sed -i "s|;*daemonize\s*=\s*yes|daemonize = no|g" /etc/php7/php-fpm.conf && \
	sed -i "s|;*listen\s*=\s*/||g" /etc/php7/php-fpm.d/www.conf && \
	sed -i "s|;*listen\s*=\s*127.0.0.1:9000|listen = 9000|g" /etc/php7/php-fpm.d/www.conf && \
	sed -i "s|;*cgi.fix_pathinfo=.*|cgi.fix_pathinfo= 0|i" /etc/php7/php.ini

RUN apk add --no-cache --update graphicsmagick curl ssmtp

RUN ln -s /usr/bin/php7 /usr/bin/php

RUN rm -rf /var/cache/apk/*

# ensure www-data user exists
RUN set -x ; \
  addgroup -g 82 -S www-data ; \
  adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 1

RUN php7 -v

CMD ["-"]