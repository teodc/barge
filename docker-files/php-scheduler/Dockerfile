ARG PHP_VERSION=7.3

FROM php:${PHP_VERSION}-cli

WORKDIR /app/acme

RUN addgroup -g 1000 barge && \
    adduser -D -g barge -u 1000 captain

RUN apt-get update \
    && pecl channel-update pecl.php.net

RUN docker-php-ext-install \
    bcmath \
    mysqli \
    opcache \
    pdo_mysql \
    pcntl

RUN apt-get install -y libicu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN apt-get install -y libzip-dev \
    && docker-php-ext-configure zip --with-libzip \
    && docker-php-ext-install zip

RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

RUN pecl install redis \
    && docker-php-ext-enable redis

# RUN apt-get install -y libgd-dev libpng-dev libjpeg-dev libfreetype6-dev \
#    && docker-php-ext-configure gd --with-gd --with-png-dir=/usr/include --with-jpeg-dir=/usr/include --with-freetype-dir=/usr/include/freetype2 \
#    && docker-php-ext-install gd

#RUN apt-get install -y libmemcached-dev zlib1g-dev \
#    && pecl install memcached \
#    && docker-php-ext-enable memcached

RUN apt-get install -y cron

RUN apt-get clean

COPY cron /etc/cron.d/

RUN chmod 0644 /etc/cron.d/cron

ENTRYPOINT ["cron"]

CMD ["-f"]
