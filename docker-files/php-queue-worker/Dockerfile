ARG PHP_VERSION=7.3

FROM php:${PHP_VERSION}-cli

RUN addgroup -g 1000 captain && \
    adduser -D -g barge -u 1000 captain

RUN apt-get update \
    && pecl channel-update pecl.php.net

RUN docker-php-ext-install \
    bcmath \
    gd \
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
    && docker-php-ext-enable mongodb \

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN apt-get install -y supervisor

RUN apt-get clean

COPY supervisord.conf /etc/supervisor/supervisord.conf
COPY conf.d/acme-worker.conf /etc/supervisor/conf.d

WORKDIR /etc/supervisor

ENTRYPOINT ["supervisord"]

CMD ["-n", "-c",  "/etc/supervisor/supervisord.conf"]
