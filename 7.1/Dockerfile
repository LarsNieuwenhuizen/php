FROM ubuntu:17.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get install -y software-properties-common
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get install -y --allow-unauthenticated php7.1-fpm php7.1-cli \
    php7.1-mbstring php7.1-mysql php7.1-pgsql php7.1-zip \
    php7.1-ldap php7.1-curl php7.1-xml php7.1-soap php7.1-gd \
    php7.1-dom php7.1-tokenizer \
    --allow-unauthenticated php7.1-redis \
    --allow-unauthenticated php7.1-xdebug \
    graphicsmagick \
    curl

RUN mkdir -p /run/php

RUN apt-get install -y ssmtp

RUN apt-get autoremove -y && \
    apt-get clean && \
    apt-get autoclean && \
    echo -n > /var/lib/apt/extended_states && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /usr/share/man/?? && \
    rm -rf /usr/share/man/??_*

RUN usermod -u 1000 www-data

CMD ["-"]